# 剑三壁纸后台管理系统

基于laravel框架，使用 `dingo/api` + `jwt` 开发的剑三壁纸后台管理系统，实现app壁纸数据增删改查管理和一些app配置管理，并提供api接口给app调用。

app仓库地址 [jiansan-swift](https://github.com/6ag/jiansan-swift) 。

![image](https://github.com/6ag/jiansan-laravel/blob/master/githubimg/example1.jpg)

![image](https://github.com/6ag/jiansan-laravel/blob/master/githubimg/example2.jpg)

## 运行环境

- Nginx 1.8+
- PHP 5.6+
- Mysql 5.7+

## 开发环境部署

本项目本地开发环境为 [Laravel Homestead](https://github.com/laravel/homestead) ，如果你还没有安装过 **Homestead** ，请参考 [laravel-china-homestead](http://laravel-china.org/docs/5.1/homestead#installation-and-setup) 。

### 安装项目

**1.克隆代码到本地**

```shell
git clone https://github.com/6ag/jiansan-laravel.git
```

**2.新建homestead站点**

使用homestead新建站点，并解析域名到项目的 `public` 目录。首先进入虚拟机环境，新建站点：

*注意：* 这里的目录要根据自己安装的路径来写的，最终解析到 `public` 目录即可，别忘了修改本地 `hosts` 文件和重启 `nginx` 。

```shell
serve www.jiansan.com /home/vagrant/Code/jiansan-laralve-master/public
```

**3.安装项目依赖包**

```shell
composer install
```

**4.拷贝环境配置文件**

拷贝 `.env` 环境配置文件，并修改数据库配置信息。

```shell
cp .env.example .env
```

**5.创建数据表**

在创建数据表前，请先确保 `.env` 文件中的数据库配置正确，并数据库已经存在。

```shell
php artisan migrate
```

**6.填充基础数据**

添加分类数据和管理员信息，填充后默认管理员账号 `admin` ， 邮箱 `admin@6ag.cn` ，密码 `123456` 。

```shell
php artisan db:seed
```

**7.注册管理员账号**

访问 `http://www.jiansan.com/` ，使用管理员账号登录即可。

### API接口文档

本项目接口文档使用 [apidoc](https://github.com/apidoc/apidoc) 生成。

**1.全局安装**

安装前请确保已经安装了 `node` ，如果是使用 `homestead` 则默认已经安装有 `node` ，可直接执行下面命令进行安装 `apidoc` 。

```shell
npm install apidoc -g
```

**2.更新文档**

在项目根目录执行下面命令更新API文档，这里的 `app/Http/Api/V1/Controllers` 是需要解析的源文件目录，指定后会递归查找符合注释条件的方法，并生成对应的接口文档。 `public/apidoc` 是存放接口文档的目录，我这里放到 `public` 目录下的原因是上线后可以直接访问哈。

```shell
apidoc -i app/Http/Api/V1/Controllers -o public/apidoc/
```

**3.注释格式**

这个请自己去看 `apidoc` 文档，每次修改注释后，需要重新生成文档都可以执行上面的命令。然后 `http://www.jiansan.com/apidoc` 即可访问文档。

## 许可

[MIT](http://opensource.org/licenses/MIT) © [六阿哥](https://github.com/6ag)


