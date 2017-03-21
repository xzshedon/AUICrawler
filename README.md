## AUICrawler
> 针对Android App 的UI遍历自动化方案 
### 遍历方案:
#### 时间模式:
* Limit ：限定遍历时长，不包括初始化应用 & 结果统计，超过规定时长后结束
* Free  ：不规定遍历时长，全部递归执行完成后结束
#### 遍历模式:
* Normal ： 按序遍历，多次／多设备执行的路径完全相同
* Random ： 随机遍历，可设置覆盖程度（0 <CoverageLever <=1）,在当前页面中随机抽取 覆盖百分比个 控件进行遍历
* Activity ： 遍历App的所有Activity（可无参数唤起的）
### 执行相关:
#### 执行前配置:
##### 配置文件
- AUICrawler
  - script
    - Setting.py
#### 执行脚本:
- AUICrawler
  - Crawler.py
#### 执行方案:
```
1. 支持多设备同时执行（多线程执行，每个设备单个线程）
2. 初始化App（针对首次启动有需滑动的Guide页的App，优先向左滑动到有可点击的控件显示；会遍历进入主页面前显示的控件至进入Setting中设置的主页面）
3. 支持执行Robotium Case（主要是用来再初始化App至满足想要的遍历条件，比如遍历前先登录 ／ 解决一些可能会影响遍历的操作）
4. 启动主页面按所选模式开始遍历
```
### 脚本结构:
#### 封装的模块:
##### 所在目录
- AUICrawler
  - module
##### 模块介绍
```
PlanInfo :  本次执行的相关配置 & 运行状态等信息 
CrawledApp :  当次执行时使用的App本身信息 & 遍历中相关状态&信息 
DeviceInfo :  每个执行的Device的本身信息 & 遍历中相关状态&信息 
PageInfo :  每次获取时的页面信息 & 遍历中相关状态&信息 
NodeInfo :  每个控件的获取时信息 & 遍历中相关状态&信息
```
#### 执行记录:
##### 目录结构
- AUICrawler
  - result
    - 20170xxxxxxxxx : 目录名称时间执行的测试计划
      - CrawlerLog.txt : 计划执行时主要Log
      - 设备ID
        - CrawlerLog.txt : 此设备执行时详细Log
        - Screenshot : 截图存储目录
        - Uidump.xml : 运行中获取页面信息生成的临时文件，计划执行结束时会删除

#### 主执行脚本： 
- AUICrawler
  - runner
    - easyrunner.py

### 开发进度:
- [x] 1.  对象架构设计
- [x] 2.  递归逻辑架构
- [x] 3.  配置信息设计
- [ ] 4.  限时模式的判断&执行框架
- [x] 5.  随机遍历模式的执行框架
- [ ] 6.  Activity模式
- [x] 7.  对Clickable的控件遍历
- [x] 8.  对LongClickable的控件遍历
- [x] 9.  对EditText的遍历
- [ ] 10. 对Scrollable的控件的遍历
- [ ] 11. 执行结果收集&统计&展示
- [ ] 12. 遍历过程中，遍历到登录页面登录功能
- [ ] 13. 命令行参数执行

> QQ：553410327 ，欢迎前辈指导，同学交流 
