
# 响应式网站设计

**目录：**

1. 前期准备

2. 如何组织项目目录结构

3. 开始编写HTML代码

4. 实现PC端的样式

5. 实现移动端的样式

6. 实现响应式广告和响应式图片

7. nodejs简介

8. 处理兼容性及多设备调试

9. 打包发布

10. IDE

11. 原型设计和切图


## 1 前期准备

本项目为一个互联网金融的响应式网站。

### 响应式网站设计

“响应式互联网设计”: [http://alistapart.com/article/responsive-web-design](http://alistapart.com/article/responsive-web-design "responsive-web-design")。

弹性布局——响应式网站。

响应式网站概念：

- 弹性网格布局；
- 弹性图片；
- 媒体查询；

### 关于浏览器

QQ浏览器的X5内核：[http://x5.tencent.com/](http://x5.tencent.com/)

### 关于媒体查询

	@media all and (min-width:800px) and (orientation:landscape){
		……
	}



## 2 如何组织项目目录结构

## 3 开始编写HTML代码

## 4 实现PC端的样式

## 5 实现移动端的样式

## 6 实现响应式广告和响应式图片

### 响应式广告实现

**完善的广告滚动组件**：

- 支持不同图片数量；
- 支持响应式布局；
- 具有良好的兼容性；

不要重复造轮子--**挑选第三方组件**：

- 使用广泛性；
- 开源且活跃；
- 文档齐全；
- 轻量级；
- Owl Carousel2组件，依赖于jQuery或Zepto；

CDN方式链接文件：
[https://cdnjs.com/](https://cdnjs.com/ "cdnjs官网")

国内可以选择BAT的CDN链接；

**流程**：

1. 引入Owl Carousel2的css和js文件；
1. 设置默认的样式文件``owl.theme.default.min.css``；
2. 书写匹配的HTML结构；
3. 调用组件，在js文件中调用；
4. API的参数设置，直接在上面组件的调用`owlCarousel()`方法里传入参数的对象形式；

### 图片的响应式

响应式图片：适配不同端图片的区别。

- JS或服务端；编写JS脚本判断浏览器的页面尺寸，或在服务器端编码验证客户端尺寸；

```

    <!--响应式图片设置js脚本-->
    <script>
        $(document).ready(function(){
            
            function makeImageResponsive(){
                var width = $(window).width();
                var img = $('.content img');
                if(width <= 480){
                    img.attr('src','img/ad001.png');
                }else if(width <= 800){
                    img.attr('src','img/ad001-m.png');
                }else{
                    img.attr('src','img/ad001-l.png');
                }
            }
            
            $(window).on('resize load',makeImageResponsive);
        })
    </script>

```

- HTML元素属性实现：srcset属性、srcset属性配合sizes；

- picture元素 + source元素：浏览器找到相适配的源文件设置；

- svg格式的图片：缩放不失真，H5-SVG图片，BAT公司的SVG图库；

**注意**：

1. srcset单独设置存在问题，需配合sizes属性；

1. Google的webp压缩格式图片；

1. 编辑器：Illustrator，在线编辑器[https://icomoon.io/](https://icomoon.io/)；

1. SVG的兼容性较好；

1. **图片压缩**：

	- SVG压缩 [http://iconizr.com/](http://iconizr.com/ "SVG压缩");
	- PNG/JPG压缩 [https://tinypng.com/](https://tinypng.com/ "png/jpg压缩");

### **具体实现**：

- polyfill方法：对于新特性，polyfill使更有能力的浏览器做得更好，逊色的浏览器也可以有自己的替代方法；
	
- 对于picture元素的polyfill库——picture库 [http://scottjehl.github.io/picturefill/](http://scottjehl.github.io/picturefill/ "picturefill");

- 引入picturefill的js库文件，用picture实现响应式图片；

## 7 Node.js简介

Node.js中文网 [http://nodejs.cn/](http://nodejs.cn/ "Node.js中文网")
> Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。Node.js 的包管理器 npm，是全球最大的开源库生态系统。

### 安装Node.js

- 检验安装：

Git Bash或 DOS 下 ： 输入 `node -v` 提示版本号 `v6.2.0`;

- hello Node.js

Git Bash或 DOS 下 ： 输入 `node test.js` 会解释执行js文件;

### npm使用

npm官网：[https://www.npmjs.com/](https://www.npmjs.com/ "npm官网")

- 检验安装：

Git Bash或 DOS 下 ： 输入 `npm -v` 提示版本号 `3.8.9`;

-下载Node.js包:

命令：`npm install jquery`，会在下载到node_modules目录下;

- package.json:

创建 package.json 文件命令：`npm init`;

```

	//创建的package.json文件
	{
	  "name": "demo",
	  "version": "1.0.0",
	  "description": "",
	  "main": "js.js",
	  "dependencies": {
	    "jquery": "^3.1.0"
	  },
	  "devDependencies": {},
	  "scripts": {
	    "test": "echo \"Error: no test specified\" && exit 1"
	  },
	  "author": "",
	  "license": "ISC"
	}

```
- 根据 package.json 下载所依赖的包：

命令： `npm i` 或 `npm i --dev` 或 `npm i --production`;

- 全局安装：

全局范围可用express，不存在与某个项目下。

命令：`npm install -g express`;

- 同步更改package.json依赖的安装：

命令：`npm install gulp --save` 生产环境依赖包；`npm install gulp --save-dev` 开发环境依赖包;

- 卸载包：

命令：`npm uninstall gulp --save-dev`;

- 更新包：

命令：`npm update jquery`;`npm update` 更新所有；

### Node.js 启动 server 服务器

http-server：基于Nodejs的轻量级HTTP服务器；GitHub地址：[https://github.com/indexzero/http-server](https://github.com/indexzero/http-server)

- 安装：`npm install http-server -g`;
- 开启服务: `http-server`;
- 关闭服务: `Ctrl + C`;

## 8 处理兼容性及多设备调试

## 9 打包发布

### 发布前优化
- 压缩：文件压缩 [http://javascript-minifier.com/](http://javascript-minifier.com/ "文件压缩")
- 合并
- 增加版本号

### 打包发布

- 主流的3个工具：

	- 自动化构建工具 Grunt、Gulp；
	- 静态资源打包工具 Webpack;

### Gulp使用

Gulp中文网 [http://www.gulpjs.com.cn/](http://www.gulpjs.com.cn/ "Gulp中文网")

> - 易于使用
> 
> 通过代码优于配置的策略，Gulp 让简单的任务简单，复杂的任务可管理。
> 
> - 构建快速
> 
> 利用 Node.js 流的威力，你可以快速构建项目并减少频繁的 IO 操作。
> 
> - 插件高质
> 
> Gulp 严格的插件指南确保插件如你期望的那样简洁高质得工作。
> 
> - 易于学习
> 
> 通过最少的 API，掌握 Gulp 毫不费力，构建工作尽在掌握：如同一系列流管道。

**使用流程**：

1. 在项目下初始化 package.json 文件；
2. 安装 Gulp 并添加到 package 开发环境依赖中, `npm install gulp --save-dev` ,检验安装 `gulp -v` ;
3. 根目录下建立 gulpfile.js 文件；
 
```

	//建立gulp依赖
	var gulp = require('gulp');
	
	//建立任务
	gulp.task('task-name',function(){
		console.log('hello gulp!');
	});

``` 

4. 运行任务 `gulp task-name`；
5. 安装 gulp 插件，`npm install gulp-rev gulp-rev-replace gulp-useref gulp-filter gulp-uglify gulp-csso --save-dev` ;

- gulp-rev：根据文件内容为文件建立版本号(哈希码)，解决文件更改后本地缓存问题；
- gulp-rev-replace：把更改过内容的文件版本号(哈希码)自动适配到index文件里的文件引用中；
- gulp-useref：以在HTML页面里添加注释的方法来进行文件合并的设置；
- gulp-filter：过滤文件操作；
- gulp-uglify：压缩js文件；
- gulp-csso：压缩css文件；

6. 在 gulpfile.js 中引用各种依赖；

``` type=javascript

	//gulpfile.js文件内容
	var gulp = require('gulp');
	var rev = require('gulp-rev');
	var revReplace = require('rev-replace');
	var useref = require('gulp-useref');
	var filter = require('gulp-filter');
	var uglify = require('gulp-uglify');
	var csso = require('gulp-csso');

	gulp.task('default',function(){
		var jsFilter = filter('**/*.js',{restore: true});
		var cssFilter = filter('**/*.css',{restore: true});
		var indexHtmlFilter = filter(['**/*','!**/index.html'],{restore: true});

		return gulp.src('src/index.html')
			.pipe(useref())
			.pipe(jsFilter)
			.pipe(uglify)
			.pipe(jsFilter.restore)
			
			.pipe(cssFilter)
			.pipe(csso)
			.pipe(cssFilter.restore)
			
			.pipe(indexHtmlFilter)
			.pipe(rev())
			.pipe(indexHtmlFilter.restore)
			
			.pipe(revReplace)
			.pipe(gulp.dest('dist'));
		
		});

```

7. 执行 `gulp default` 开始打包 。

其他gulp插件：

- gult-watch：更改文件,自动打包；GitHub地址 [https://github.com/floatdrop/gulp-watch](https://github.com/floatdrop/gulp-watch "gult-watch")
- gulp-postcss：css文件添加前缀等一些处理；GitHub地址 [https://github.com/postcss/gulp-postcss](https://github.com/postcss/gulp-postcss "gulp-postcss")
- gulp-concat：文件合并；GitHub地址 [https://github.com/contra/gulp-concat](https://github.com/contra/gulp-concat "gulp-concat")
- gulp-responsive：生成响应式图片；GitHub地址 [https://github.com/mahnunchik/gulp-responsive](https://github.com/mahnunchik/gulp-responsive "gulp-responsive")

## 7 nodejs简介

## 8 处理兼容性及多设备调试

## 9 打包发布

## 10 IDE

## 11 原型设计和切图





