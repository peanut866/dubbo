
## 编译过程

- 从gitee中将dubbo 的 2.7.8 分支拉取下来
    ```
   git clone --branch dubbo-2.7.8 https://gitee.com/apache/dubbo.git
    --branch 是选择分支或者标签
    ```
- 执行以下命令进行 构建以及创建.idea文件夹做准备
     ```
      cd dubbo/
      mvn install -Dmaven.test.skip=true
      mvn idea:idea(不能执行)
     ```
    执行到 mvn idea:idea时，发生了空指针错误，没办法搞了，强行将项目导入了进去(import 不是 open)
    (project->new -> project from Existing Source);
    以后不要执行 mvn idea:idea
    
- 导入后，maven项目，无法进行代码引用跳转，所以需要指定sources 目录。两种方式：
  1. 通过 file -> project structure -> module -> 选择项目的 source 目录（选择java 文件夹，不能选最顶层）。
    同时还要选择 Language Level 最小选1.8
  2. 第二种，直接在左侧目录的右键，mark directory as -> Sources Root
    
- 导入后，所有的module都无法解析maven，报错manve与 idea版本不适配.
    我使用的maven-3.6.2， idea-2019.2 。
    ```
    class org.jetbrains.idea.maven.server.embedder.CustomMaven3Modellnterpolator2 tried to access method 'void
    org.apache.maven.model.interpolation.StringSearchModelnterpolator.interpolateObjectliava.ang.Object,org apache.mavenmodelNode jv.iofF leorg.apache.maven.model.building.ModelBuildingRequest,org.apache.maven.modelbuilding.ModelProblemCollector)"
    (orgietbrains.idea.maven.severembedder.CustomMaven3ModeInterpolator2 and org apachermaven.modelinterpolation.StringSeachMocdelterpolatorare nuLmamedmodule of loader 'app')
    ```
  解决方法是使用搭配的maven版本(3.6.1)，而我没有重新下载，而是在 file->setting->Build,Execution,Deployment -> maven -> maven home directory 中
  选择idea 自带的maven版本。

 
