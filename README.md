# webpack_ecmascript
webpack build javascript6

##webpack + es6 构建代码

###环境搭建步骤
* 安装node
* win+R -> cmd,切换到本地项目目录
* 在项目目录执行命初始化包管理文件  npm init 生成package.json,在命令行根据提示输入相关信息
* 安装webpack到项目目录 npm install webpack --save-dev,安装依赖文件，并将依赖关系写入
package.json中
* 安装代码编译器，目前es6在很多浏览器还不支持，需要转码
    * npm install babel-loader --save-dev
    * npm install babel-core --save-dev
    * npm install babel-preset-env --save-dev
    
* 创建打包脚本文件
   ```````````````````
    const path = require('path');
    module.exports = {
        entry:path.resolve(__dirname,'src/pixiEngine/Main.js'),
        output: {
            filename: 'bundle.js',
            path:path.resolve(__dirname,'build'),
        },
        module:{
            rules:[
                {
                    test:/(\.jsx|\.js)$/,
                    use:{
                        loader:"babel-loader",
                        options:{
                            presets:[
                                "env"
                            ]
                        }
                    },
                    exclude:path.resolve(__dirname,"node_modules"),
                    include:path.resolve(__dirname,"src")
                }
            ]
        }
    }
     ```````````````````
     
* 打包时在当前项目的命令行执行以下命令：npm run build//这个命令来自package.json中的script中，
  如果没有配置，可以直接执行webpack即可进行打包
