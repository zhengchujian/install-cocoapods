# install-cocoapods
安装使用cocoapods

  1.什么是cocoapods
    CocoaPods是一个用来帮助我们管理第三方依赖库的工具。它可以解决库与库之间的依赖关系，下载库的源代码，同时通过创建一个Xcode的workspace来将这些第三方库和我们的工程连接起来，供我们开发使用。使用CocoaPods的目的是让我们能自动化的、集中的、直观的管理第三方开源库。
    
  2.安装Ruby运行环境(以下代码区域，带有 $ 打头的表示需要在控制台（终端）下面执行（不包括 $ 符号）)
    在安装CocoaPods之前，首先要在本地安装好Ruby环境。
      (1)安装系统需要的包：先安装 [Xcode](http://developer.apple.com/xcode/) 开发工具，它将帮你安装好 Unix 环境需要的开发包。
      (2)安装RVM
        $ curl -L https://get.rvm.io | bash -s stable
        载入RVM环境：$ source ~/.rvm/scripts/rvm
        检查安装是否正确：$ rvm -v
                          rvm 1.22.17 (stable) by Wayne E. Seguin <wayneeseguin@gmail.com>, Michal Papis <mpapis@gmail.com> [https://rvm.io/]
      (3)用RVM安装Ruby环境：$ rvm install 2.0.0
      (4)设置Ruby版本：$ rvm 2.0.0 --default
        测试是否正确：$ ruby -v
                      ruby 2.0.0p247 (2013-06-27 revision 41674) [x86_64-darwin13.0.0]
                      $ gem -v
                      2.1.6
      (5)Ruby的默认源使用的是cocoapods.org，国内访问这个网址有时候会有问题，网上的一种解决方案是将远替换成淘宝的，替换方式如下：
        $gem source -r https://rubygems.org/
        $ gem source -a https://ruby.taobao.org
        验证是否替换成功：$ gem sources -l
        正常的输出结果：
                          *** CURRENT SOURCES ***
                          https://ruby.taobao.org
 
  3.下载安装cocoapods：$ sudo gem install cocoapods
  
  4.Podfile（控制cocoapods该下载什么）
    (1)创建Podfile：在终端进入(cd)到项目所在目录，利用vim创建Podfile：$ vim Podfile
    (2)（以下载AFNetworking为例）在Podfile输入以下文字：
              platform :ios, '7.0'
              pod "AFNetworking", "~> 2.0"
    (3)保存退出（esc退出编辑模式，:wq保存退出）
    (4)下载Podfile里的内容：$ pod install
    
  5.工程目录下会自动生成一个.xcworkspace和“Podfile.lock”和一个文件夹“Pods”。以后打开项目就用 PROJECTNAME.xcworkspace 打开。
  
  6.正确编译运行一个包含CocoPods类库的项目
    进入终端，进入项目所在的目录（Podfile同一目录），输入：$ pod update
