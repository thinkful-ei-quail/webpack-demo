npm init -y     //This creates our package.json file
npm install jquery    //This installs Jquery
npm install --save-dev webpack webpack-cli webpack-dev-server html-webpack-plugin style-loader css-loader file-loader   
//This installs everything we need for webpack


Create webpack.config.js  file and paste this into it:

const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: __dirname + '/dist',
    filename: 'index_bundle.js'
  },
  mode: 'development',
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html',
    })
  ],
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          'style-loader',
          'css-loader'
        ]
      },
      {
        test: /\.(png|svg|jpg|gif)$/,
        use: [
          'file-loader'
        ]
      }
    ]
  }
}



Update package.json scripts to this:

"scripts": {
  "start": "webpack-dev-server", 
  "build": "webpack --mode production"
}