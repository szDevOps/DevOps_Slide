## 基于OSS的DevOps方案



### DevOps平台搭建及技术选型

私有部署GitLab，那么首先需要考虑的是服务器的硬件投入和人力资源成本。

硬件投入方面，GitLab的软件要求较高。想要部署GitLab平稳运行，需要至少8GB RAM、Quad Core CPU以及至少500GB SSD硬盘。这只是硬件设备的基本开销。人力资源成本方面，要有专业的DevOps工程师来部署和维护GitLab私有服务器，这些成本会随着规模的扩大不断增加。


#### 成本和收益的考虑
GitLab私有部署的费用取决于开发规模和团队的需求。如果公司规模较小，可以选择开源版本的GitLab进行自行部署，这样可以最大程度地降低硬件投入和人力资源成本。随着规模的扩大，可以选择购买GitLab企业版的方案，可以获得更全面的技术支持和更多的高级功能，并且可以通过云计算模式让整个部署更加灵活和可控制。


### 预期目标

1、源代码管理
借助 GitLab 实现源代码托管，私有化部署版本，创建项目，创建用户组，分配权限，项目的维护变更，团队间的协作等。

2、 自动化部署
项目指定分支(源代码)产生变更时(如签入)，自动化编译并发布到指定服务器中部署，借助GitLab-runner实现持续及时部署，供用户访问项目更新的站点，这里用在开发环境。


### 环境说明
硬件基本要求：4核8G
RHEL8 Linux operating system：这里用GitLab官网提到的 AlamLinux8
GitLab v15：用于源代码托管
Git：用于远程自动拉取源代码
dotnet 6.0：测试站点的运行环境
GitLab-runner：实现自动化部署的应用
最主要的两个安装 GitLab、GitLab-runner 通常会分开部署，这里计划所有的安装均在同一台服务器中。


### 自动化测试框架

Web应用功能测试
Selenium
最常用的 Web 应用程序自动化测试框架之一。它支持多种编程语言，包括 Java、Python、C# 和 JavaScript。


自动化测试框架
Jenkins 
CI/CD最流行的工具当属Jenkins和Gatlab。Jenkins是一款开源 CI&CD 软件，用于自动化各种任务,包括构建、测试和部署软件。
与GatHub集成，GatHub 开发中用来做 Code Review 和 issue 跟踪，Jenkins 主要是用来保证测试和部署。

移动应用程序测试
Appium
Appium 是一个用于移动应用程序测试的开源自动化测试框架。它支持多种移动平台，包括 iOS、Android 和 Windows。


### 常用的压力测试工具

Apache JMeter
JMeter是一款开源免费的压测产品，最初被设计用于Web应用功能测试使用，如今JMeter被广泛用于性能测试。


locust
Locust 完全基本 Python 编程语言，采用 Pure Python 描述测试脚本，并且 HTTP 请求完全基于 Requests 库。除了 HTTP/HTTPS 协议，Locust 也可以测试其它协议的系统，只需要采用Python调用对应的库进行请求描述即可。但是需要手工编写脚本，有一定的难度。


Webbench
Webbench是著名的压力测试工具，它能测试处在相同硬件上，不同服务的性能以及不同硬件上同一个服务的运行状况。


Apache Bench
Apache Bench是Apache服务器的一个web压力测试工具，简称ab。它可以模拟多个用户对某个网站发起访问。

### 代码质量检测和代码安全检查工具

SonarQube
SonarQube是一个开源的代码质量检测和代码安全检查工具，支持多种语言，提供检查代码bug、漏洞，检查代码规范，一键修复历史债务等功能。