**第五章 设计与实现**

 

5.1界面设计与实现

 

本网站的主界面设计通过进行首页、上传、登录、注册、用户、反馈和建议。界面设计如图5.1所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

图5.1　系统首页

 

5.2前台功能设计

 

本前台主要功能设计详细的说明。

5.2.1用户注册界面

1．注册

通过用户注册实现。其界面的如图5.2所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image004.jpg)

图5.2　用户注册模块

 

**（****1****）代码**

<form role="form" method="POST" enctype="multipart/form-data" novalidate>

<fieldset>

<div class="form-group">

<label for="input_name"><span class="glyphicon glyphicon-user"></span>&nbsp;{{ form.name.label }}</label>

{#"昵称" #}

{{ form.name }}

{% for err in form.name.errors %}

<div class="col-md-12"><p style="color: red">{{ err }}</p></div>

{% endfor %}</div>

<div class="col-md-12" id="error_name"></div>

<div class="form-group">

<label for="input_email"><span class="glyphicon glyphicon-envelope"></span>&nbsp;{{ form.email.label }}</label>

{#"邮箱"#}

{{ form.email }}

{% for err in form.email.errors %}

<div class="col-md-12"><p style="color: red">{{ err }}</p></div>

{% endfor %}</div>

以上的方法是一样的，不过只是不同名称如下，

<div class="col-md-12" id="error_email"></div>

​       {{ form.phone.label }}

​            {{ form.phone }}

​            {% for err in form.phone.errors %}

​            {% endfor %}

​            {#"手机"#}

 <div class="col-md-12" id="error_phone"></div>

​        {{ form.face.label }}

​            {% if user.face %}

​                <img src="{{ url_for('static', filename='uploads/users/' + user.face) }}"

​                     style="width: 100px;" class="img-responsive img-rounded">

​            {% else %}

​                <img data-src="holder.js/100x100" class="img-responsive img-rounded">

​            {% endif %}

​            {{ form.face }}

​            {% for err in form.face.errors %}

​            {% endfor %}

​            {#上传头像#}

​        <div class="col-md-12" id="error_face"></div>

​        {{ form.info.label }}

​            {{ form.info }}

​            {% for err in form.info.errors %}

 

​            {% endfor %}

​        {{ form.csrf_token }}

​        {{ form.submit }}

 

2．登录和验证

**（1）验证**

通过用户登录实现，而当输入时，已注册过后，邮箱和手机不能再填同样重复信息。如果用户不存在，会提示不存在。其界面如图5.3所示

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image006.jpg)

图5.3　用户验证图

 

**（****2****）****登录**

输入时注意的是密码，切记密码。其界面如图5.4所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image008.jpg)

图5.4　用户登录模块

 

3．用户修改和退出

**（****1****）****修改信息**

已注册过的用户同时直接登录本网站后，就可以看到用户信息，然后点击用户中心和修改密码操作即可，在这此本身页面时，提高了很多方便操作。其界面如图5.5所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image010.jpg)

图5.5　用户修改信息模块

 

用到了Session信息，是为了用户账号安全性，如想关闭浏览器的话，可以建议使用退出登录即可，这样一来就能清除了，不会留下痕迹。

 

**（****2****）****退出**

点击退出即可.其界面如图5.6所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image012.jpg)

图5.6　退出模块

 

5.2.2首页界面

1．首页

为了简洁界面，适意简化，给用户展示作用。其界面如图5.7所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image014.jpg)

图5.7　首页模块

2.本地地址

为什么就写127.0.0.1：5000，因为它自动默认成为本地地址，其实由于flask出于安全考虑而执行默认行为，不允许外部客户端访问。其界面如图5.8所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image016.jpg)

图5.8　首页模块

如想外部想要访问本网站，只有设置一行代码如：

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image018.jpg)现在，站点更像真实网站了。

5.2.3上传界面

1．上传

分享视频给任何人看，就用上传来添加。其界面如图5.9所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image020.jpg)

图5.9　上传模块

5.2.4用户界面

1．用户

当操作时使用了合并的前端，方便给用户选择上下窗口，而不需要一个一个打开，如此很完善。其界面如图5.10所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image022.jpg)

图5.10　用户模块

 

5.2.5搜索界面

1．搜索

通过这设计来给用户快速搜索，而且升级了功能上传。其界面如图5.11所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image024.jpg)

图5.11　搜索模块

 

5.2.6电影分页模块

1．电影

嘻嘻，看着网站好像能吸引用户喜爱，要是我肯定很喜欢它，因为图片很酷哦。本网站采用筛选分页来设计。这么多电影，找来找去会很怒的，选中想看的某部电影，筛选分页会帮用户实现信息。其界面如图5.12所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image026.jpg)

图5.12　电影模块

 

5.2.7播放界面

1．播放

​     别小看播放功能少，播放电影作用很大，为什么？为了能够用户满意程度，我们设计了播放模块，让用户看清晰，减少卡顿、评论、收藏和弹幕。为了更多电影观众提供一个相互交流的桥梁，能通过看到与观众交流自己的观影后感。弹幕是一个主流的弹幕视频，而且是一个革新弹幕技术。看过程中，把自己想法表达出来通过文字输入形式，然而会出现屏幕上，可以在评论上，任何写出感受。这些是一种庞大的文字信息资源。总的来说，是一个很好的网络公共平台的。其界面如图5.13所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image028.jpg)

图5.13播放模块

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image030.jpg)

图5.14弹幕模块

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image032.jpg)

图5.15评论模块

5.2.8反馈及意见界面

1．反馈

通过反馈问题，我们可以及时改进。其界面如图5.16所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image034.jpg)

图5.16　反馈及意见模块

2．意见

很宝贵的意见，这样让我们做好更新和维护。更好给用户满意程度。

5.2.9热映界面

1．已上映

通过热映分成两种，一是已上映，二是即将上映。为了给用户更加方便操作，用户可以及时了解的时间和故事，还可以点击播放预告视频，非常精彩。其界面如图5.17所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image036.jpg)

图5.17　已上映模块

 

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image038.jpg)

图5.18　播放已上映模块

2．即将上映

通过热映分成两种，一是已上映，二是即将上映。用户看好电影或者收藏电影，可以及时了解的时间和故事，还可以点击播放预告视频，非常精彩。如有更新的电影，我们可以更新传送信息。其界面如图5.19所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image040.jpg)

图5.19　即将上映模块

 

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image042.jpg)

图5.20　播放已上映模块

5.2.10新闻资讯界面

1．影视资讯

通过新闻资讯分成两种，一是影视资讯，二是新闻右列。为了给用户更加方便操作。用户可以查看更新新闻资讯，还可以点击另一个页面，好奇，八卦，影视等等的事情。其界面如图5.21所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image044.jpg)

图5.21　影视资讯模块

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image046.jpg)

图5.22　页面资讯模块

2．影视资讯

通过新闻资讯分成两种，一是影视资讯，二是新闻右列。为了给用户更加方便操作。新闻右列是设计给用户美观和风格。其界面如图5.23所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image048.jpg)

图5.23　右列模块

5.3后台功能设计

 

5.3.1管理员弹出登录界面

1．admin登录

管理员登录实现形式。其界面如图5.24所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image050.jpg)

图5.24　admin登录模块

 

5.3.2标签管理界面

1．标签

先把标签添加完后，电影管理就能添加了。其界面如图5.25所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image052.jpg)

图5.25标签管理模块

 

5.3.3电影管理界面

1．电影

在电影管理模块中是电影基本信息，添加电影后，由管理员来管理电影，有新电影及时更新，给浏览者带来更多的娱乐。其界面如图5.26所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image054.jpg)

图5.26　电影管理模块

 

**（1）代码**

<div class="form-group">

​    <label for="input_title">{{ form.title.label }}</label>

​    {#"请输入片名！"#}{{ form.title }}{% for err in form.title.errors %}{% endfor %}

</div>

<div class="form-group">

​    <label for="input_url">{{ form.url.label }}</label>

​    {#"上传视频">#}{{ form.url }}{% for err in form.url.errors %}{% endfor %}

</div>

<div class="form-group">

​    <label for="input_info">{{ form.info.label }}</label>

​    {#"简介"#}{{ form.info }}{% for err in form.info.errors %}{% endfor %}

</div>

<div class="form-group">

​    <label for="input_logo">{{ form.logo.label }}</label>

​    {#"封面"#}{{ form.logo }}{% for err in form.logo.errors %}{% endfor %}

<img data-src="holder.js/262x166" style="margin-top:5px;" class="img-responsive" alt="">

</div>

<div class="form-group">

​    <label for="input_star">{{ form.star.label }}</label>

​    {{ form.star }}{% for err in form.star.errors %}{% endfor %}

​    {#<option value="1">1星</option>#}

​    {#<option value="2">2星</option>#}

​    {#<option value="3">3星</option>#}

​    {#<option value="4">4星</option>#}

​    {#<option value="5">5星</option>#}

</div>

<div class="form-group">

​    <label for="input_tag_id">{{ form.tag_id.label }}</label>

​    {{ form.tag_id }}{% for err in form.tag_id.errors %}{% endfor %}{#"类型">#}

</div>

<div class="form-group">

​    <label for="input_area">{{ form.area.label }}</label>

​    {{ form.area }}{% for err in form.area.errors %}{% endfor %}{#"请输入地区！"#}

</div>

<div class="form-group">

​    <label for="input_length">{{ form.length.label }}</label>

​    {{ form.length }}{% for err in form.length.errors %}{% endfor %}{#"请输入片长！"#}

</div>

<div class="form-group">

​    <label for="input_release_time">{{ form.release_time.label }}</label>

​    {{ form.release_time }}{% for err in form.release_time.errors %}{% endfor %}

​    {# "请选择上映时间！">#}

</div>

</div>

<div class="box-footer">

​    {{ form.csrf_token }}

{{ form.submit }}

 

5.3.4上传管理界面

1．上传列表

在从前台上传到后台管理显示列表，为了给后台实现操作，管理员有权限是否需要还是删除。其界面如图5.27所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image056.jpg)

​                    图5.27　上传管理模块

 

5.3.5三大管理界面

1．权限。角色和管理员

说到这三大管理，是为了关联到三个紧密，首先添加权限信息，接下来复制网址到地址内容即可。管理员设计是为了分担，给普通管理员不同任务。其界面如图5.28所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image058.jpg)

图5.28权限管理模块

2．权限。角色和管理员

角色管理是分配普通管理员任务工作，如管理员负责多少管理就多少管理。在操作权限下列表，可以多选也可以单选。其界面如图5.29所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image060.jpg)

图5.29角色管理模块

3．权限。角色和管理员

管理员是一个更好管理前后台的操作，分为两种情况，其一，不用设置权限，可以用超级管理员，其二，所用设置权限，已添加好的角色，就选择普通管理员。其界面如图5.30所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image062.jpg)

图5.30管理员管理模块

\4. 看得出来，普通管理员1访问不了添加电影。其界面如图5.31所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image064.jpg)

图5.31不能访问管理模块

5.3.6用户管理界面

1．用户

用户管理可以查看用户详细信息。其界面如图5.32所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image066.jpg)

图5.32用户管理模块

5.3.7评论管理界面

1．评论

方便管理评论信息，如有不符内容或者敏感词语，将会及时删除。其界面如图5.33所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image068.jpg)

图5.33评论管理模块

 

5.3.8收藏管理界面

1．收藏

查看用户收藏信息。其界面如图5.34所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image070.jpg)

图5.34收藏管理模块

 

5.3.9日志管理界面

1．日志

查看用户日志操作信息。其界面如图5.35所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image072.jpg)

图5.35日志管理模块

5.3.10反馈及意见管理界面

1．反馈及意见

查看反馈和意见信息，以便管理员及时改进，接受用户的建议，不断地更新完善。其界面如图5.36所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image074.jpg)

图5.36反馈及意见管理模块

5.3.11热映界面

1．已上映

添加已上映的信息，管理员会满足用户的需求内容。其界面如图5.37所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image076.jpg)

图5.37已上映管理模块

 

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image078.jpg)

图5.38已上映列表管理模块

2．即将上映

添加即将上映，如有更新的电影，管理员会及时添加，传送到前台的信息。其界面如图5.39所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image080.jpg)

图5.39即将上映管理模块

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image082.jpg)

图5.40即将上映列表管理模块

5.3.12新闻资讯管理界面

1．影视资讯

新闻，影视新闻，八卦等等，管理员会搜索和查找资料，然后添加一些信息，不断地更新改进。其界面如图5.41所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image084.jpg)

图5.41 影视资讯管理模块

 

 

 

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image086.jpg)

图5.42 影视资讯列表管理模块

2．新闻右列

管理员设计为了给用户明显的地方，好让他们简单知道这的。实现了美观和风格。其界面如图5.43所示。

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image088.jpg)

图5.43新闻右列管理模块

![img](file:///C:/Users/10843/AppData/Local/Temp/msohtmlclip1/01/clip_image090.jpg)

图5.44新闻右列列表管理模块

 

 

 

 

 

 

 