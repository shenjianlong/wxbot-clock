
#wxbot-clock
基于wxbot框架实现的查卡打卡机器人。
wxbot框架：[点击跳转至liuwons/wxBot](https://github.com/liuwons/wxBot/)

###1. 背景
该机器人专为微信早起群“早起自律小分队”定制，基于群内早起规则实现自动查卡并推送功能。

####1.1早起规则

- 每天早7点半前在群里发图片打卡，图片需证明已起床。
- 每隔两天统计一次两天打卡情况，若连续两天未早起将被踢出群组。
- 每隔四天统计一次四天打卡情况，若在前两天和后两天中均有未打卡/迟到情况（又称偷懒），将被踢出群组。
- 支持特殊情况请假，支持时差党使用当地时间。

####1.2 支持功能
- 记录群成员早上打卡时间（根据规则只识别图片，无法识别文字，语音以及表情）
- 每天早上7点半发送迟到分割线（从早安语中随机任选）。
- 每天晚上8点推送近期查卡情况，包含当天的查卡，前一天的查卡，两天中需要被踢成员的统计结果，四天中需要被踢成员的统计结果。（因时差党的存在，每晚8点的查卡结果较为准确。）
- 可使用命令查询打卡情况，包括当天的查卡，前一天的查卡，某一天的查看，两天的查卡统计，四天的查卡统计，个人的查卡，他人的查卡。
- 可转换时差党的打卡时间为当地时间（根据昵称中包含的时差进行转换）
- 可使用命令当天请假（无法销假，无法连续请假）
- 可躺平任调戏（使用图灵api实现）
####1.3 尚未支持功能
- 成员连续打卡天数统计
- 改名后重新登录数据不丢失
- 暂未支持用户名中表情转换
-  以及其他未发现bug



###2. 开发
####2.1 环境与依赖

此版本只能运行于Python 2环境 。
wxBot 用到了Python requests , pypng , Pillow 以及 pyqrcode 库。
wxbot-clock用到了codecs库。
####2.2 运行
代码的修改可直接参考wxbot框架。添加个人函数实现定制机器人。
使用python main.py后扫码即可登录。（此处建议参考wxbot框架使用说明）

###3. 使用说明
|命令格式|例如|返回内容|备注
|---|---|---|---|
|我的打卡|我的打卡|个人最近四天的打卡情况|
|@xx的打卡|@楠的打卡|xx最近四天的打卡情况|此处必须为at方生效，直接输入无效|
|请假[空格]请假原因|请假 忘记打卡|请假成功|若格式错误会返回请假失败提示
|两天的查卡|两天的查卡|群内最近两天的查卡统计结果|不包含每日查卡结果
|四天的查卡|四天的查卡|群内最近四天的查卡统计结果|只包含偷懒人和统计，不包含每日及每两日结果
|查卡|查卡|当天的查卡结果|实时刷新，截止到查询时间的结果
|昨天的查卡|昨天的查卡|昨天的查卡结果
|[日期]的查卡|20170101的查卡|这个日期的查卡结果|格式为8位年月日

###4. 成果展示
![长图，点击查卡](http://img.blog.csdn.net/20170107185747785?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc2F0YW5u/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

###5.项目收获
1. 每过半年就会觉得上一个版本的设计方式不忍直视。
但很庆幸这说明这半年我不是一无所获。
2. 将1.0版本的文本记录更改为数据库记录，查询更方便，不会丢失数据。
但模块分割仍有些难理解，仍需继续改进。
3. deadline永远是第一生产力。
4. 早起是一件好事，也是一件难事。

###6.欢迎加入早起团
1. 小萌机器人微信号：xiaomengrobot
2. 个人微信公众号：小南瓜的每日一记
3. 早起自律小分队二维码：
![二维码](http://img.blog.csdn.net/20170107190525585?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc2F0YW5u/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)





