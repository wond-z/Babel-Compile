# Babel-Compile
使用babel将ES6语法编译为ES5语法（兼容低版本浏览器）

## 第一步:

新建一个项目文件，文件名称随意,进入文件,使用命令初始化， `npm init -y`，执行命令后会多一个文件 `package.json`

## 第二步:

新建一个文件夹src(名称随意)，把需要转换的JS文件放在里面

## 第三步:

安装babel相关安装包

```shell
npm install --save-dev @babel/core @babel/cli @babel/preset-env
npm install --save @babel/polyfill
```

## 第四步:

在根目录下新建一个文件 `babel.config.json` ，写入内容，主要是配置浏览器的最低兼容版本

```json
{
  "presets": [
    [
      "@babel/env",
      {
        "targets": {
          "edge": "17",
          "firefox": "60",
          "chrome": "67",
          "safari": "11.1",
        },
        "useBuiltIns": "usage",
      }
    ]
  ]
}
```

## 第五步:

在命令窗口输入 `.\node_modules\.bin\babel src --out-dir dist --presets=@babel/preset-env`

`src` 是你需要转换的文件夹名称 `dist` 是放置转换后的文件名称
转换成功后,项目文件中就多了一个dist文件夹，里面的JS文件就是转换后的
如果不想每次转换都输入这么长一串命令,可以在 `package.json` 中设置替换命令,设置后每次输入`npm run babel`就能转换了

```json
"scripts": {
    "babel": ".\\node_modules\\.bin\\babel src --out-dir dist --presets=@babel/preset-env",
    "test": "echo \"Error: no test specified\" && exit 1"
},
```

> 以上转换是没有经过代码压缩的,如果需要代码压缩,可以加入webpack来实现
