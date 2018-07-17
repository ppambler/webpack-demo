# webpack-demo
## ★postcss-loader

### ◇**postcss.config.js**

不需要`parser:'sugarss'`，如果你想把首页追加的样式压缩了，即去掉空格等字符，就把这个`'cssnano': {}`注释给去掉 

## ★使用webpack很重要的图

![](http://otty6pwsj.bkt.clouddn.com/18-7-17/57369133.jpg)



## ★Q&A

### 1.为什么我无法使用`npx`？

> npx 是跟随 npm@5.2.0 发布的，使用5.2.0版本之后的 npm，会自动帮你安上 npx
>
> 查看：https://juejin.im/post/5a9f5c43f265da238155293e

而我的则是npm@3.10.9……

### 2.「package.json」 存在的意义？

> 一般记录了项目的配置信息，包括名称、版本、许可证等元数据， 也会记录所需的各种模块，包括 执行依赖，和开发依赖， 以及scripts字段 

### 3.为什么我的「package.json」没有`dependencies`这个字段的？

> 用npm安装模块时加上--save-dev，就能在package.json文件中写入依赖。如安装moment,则执行npm install moment --save-dev。 
>
> 参考这个：http://www.imooc.com/qadetail/120705

我在按照这个「postcss.config.js」添加依赖的时候，直接就是 :

```bash
npm i postcss-import
```

所以这就是为什么你在安装某个东西的时候，会有这个 `--save-dev`的原因。突然发觉这个参考答案有问题啊！

应该是 `--save`才对吧！

那么问题又来了——[npm --save-dev --save 的区别](https://blog.csdn.net/juzipchy/article/details/65653683)

所以有：

> `dependencies`字段指定了项目运行所依赖的模块，`devDependencies`指定项目开发所需要的模块。

可这样问题又来了——「开发时依赖和运行时依赖，有啥区别？」参考这个：[依赖的类型](https://yarnpkg.com/lang/zh-hans/docs/dependency-types/)

> - `dependencies`
>
>   这是所谓的常规依赖，确切地说，是代码运行时所需要的（比如 React 和 immutableJS）。
>
> - `devDependencies`
>
>   这是开发依赖，就是那些只在开发过程中需要，而运行时不需要的依赖（比如 Babel 和 Flow）。 
>
> - ……

大致理解一下就是，你想让他人访问你的首页，那么有些诸如jQuery等库，诸如vue.js等框架（关于框架和库的区别：[jQuery 是库（library）还是框架(framework)?](https://www.zhihu.com/question/30693031)），你的首页要跑起来，那么这些东东就得扔到 `dependencies`字段里去说明这是哪个版本的，而Babel这些命令行工具就扔到`devDependencies`这里去说明工具的版本

所以有个「package.json」文件很重要啊！尤其是有「依赖味道」的字段特别重要……



