## yii2 统一管理 crontab 执行脚本

### 介绍
将 yii2 需要执行的脚本，统一接管到一个类中进行处理，方便管理。代码是在别人的基本上修改所得，虽然名为 yii2 的脚本，但是想修复为别的框架的代码也是非常容易的，只要注意代码中的几个属性的赋值即可。

### 使用
### 添加别名
在 console 模块的 main.php 配置文件中添加别名指定 yii 脚本的路径：
```php
'aliases' => [
    '@runnerScript' => dirname(dirname(__DIR__)) . '/yii'
],
```
### 添加执行命令
在 cronJobController::run() 中添加一条命令：
```php
$this->command('test/test321')->schedule('*/7 * * * *')->parse();
```
### crontab 添加命令
```
*/1 * * * * * /usr/local/php/bin/php /www/advanced/yii cron-job/run
```
