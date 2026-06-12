---
title: "Firefox doesnt do IE"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-01-19
```
Business Server Page (BSP) Error

What happened?

Call of BSP page terminated due to error.
 
Note

    * Following error text processed in system:
      <htmlb:content>: (*) This browser is not supported. IE as of 5.50 and Netscape as of 6.20 are supported for design2000

 

Error Type: 

Your SAP Business Server Pages Team
```

Has anyone here that use linux have issues with sites not compatible with firefox? How you get such issues resolved?

---

### Post by OldTimeTech on 2007-01-19
There is an add-on called IE Lite, that allows you to right click on the page that doesn't work and use the IE lite to be able to see everything on it.

---

### Post by teaker1s on 2007-01-19
problem is that certain webmasters use specific internet explorer tricks on their sites, now there are several routes you could try
1) another browser such as opera, may just be firefox issue
2)use **wine** to run internet explorer-my experience was it was unstable but worked:)

---

### Post by mikewhatever on 2007-01-19
Very few sites do not support Firefox these days. If you need such a site, try to install IE browser, or use an IE extention for Firefox. I'll look for the link for you.

---

### Post by SunnyRabbiera on 2007-01-19
If a website doesnt support firefox, dont use it unless its really bimportant...
Opera can do borwser identification for you, plus there is an extention ifor firefox that masks ff as IE.

---

### Post by mikewhatever on 2007-01-19
Here you go [https://addons.mozilla.org/firefox/1419/](https://addons.mozilla.org/firefox/1419/)

---

### Post by tonyr1988 on 2007-01-19
You may also wanna check out [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by bollix47 on 2007-01-19
> **mikewhatever said:**
> Here you go [https://addons.mozilla.org/firefox/1419/](https://addons.mozilla.org/firefox/1419/)

IE Tab is not available for Linux

You could try the [User Agent Switcher.]("http://chrispederick.com/work/useragentswitcher/")

---

### Post by ciscosurfer on 2007-01-19
read next post

---

### Post by ciscosurfer on 2007-01-19
Try the User Agent Switcher: [https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)

OR

Keep a Windows partition around so you can access sites using IE7 on Windows (I know, I know...but if you can't access a certain site using Linux, use what you have lying around--and was once useful will become useful again. I have friends, including myself, who use Ubuntu as our main OS, but when it comes to certain sites, etc., Windows just does a better job and handles it better and is more effective.)

:-)

---

### Post by mikewhatever on 2007-01-19
> **bollix47 said:**
> IE Tab is not available for Linux

You could try the [User Agent Switcher.]("http://chrispederick.com/work/useragentswitcher/")

Right, thanks for pointing out.

---

### Post by teaker1s on 2007-01-19
ie view lite plugin works with firefox and linux

---

### Post by in_flu_ence on 2007-01-19
Really appreciate all your help. fantastic to see replies within minutes. Nevertheless, the user agent thingy doesn't work with firefox 2.0.0.1

So i guess i have to wait till the thing is updated.

---

### Post by bollix47 on 2007-01-19
> **teaker1s said:**
> ie view lite plugin works with firefox and linux


How?  Using Wine?  I just installed it to try it out and of course it won't start iexplore from the windows partition.

---

### Post by teaker1s on 2007-01-19
my mistake it installs with no errors in firefox linux so I though it worked.](*,) 
I have successfully wine and ie, problem I had was stability

---

### Post by in_flu_ence on 2007-01-19
Yah I am no big fan about wine though. Maybe i m just a newbie. I just don't get confident with installing stuff using wine and run them using wine and eventually removing them.

Any good guide on that? but I do installed virtualbox tonight to get a windows virtual partition. The thing about IE is that some internet banking facilities can only run in windows. Poor choice. so it just make me think of switching bank to be a complete LINUX user:P

---

### Post by halitech on 2007-01-19
> **teaker1s said:**
> 
2)use **wine** to run internet explorer-my experience was it was unstable but worked:)

so, pretty much the same as in windows ;)

---

### Post by bollix47 on 2007-01-19
> **in_flu_ence said:**
> Really appreciate all your help. fantastic to see replies within minutes. Nevertheless, the user agent thingy doesn't work with firefox 2.0.0.1

So i guess i have to wait till the thing is updated.


You can use one of two extensions to force that extension to install:

[URL="http://users.blueprintit.co.uk/~dave/web/firefox/nightly"]Nightly Testing Tools
[/URL]

[Mr Tech's Local Install]("https://addons.mozilla.org/firefox/421/")


OR

You can type about:config in the address location and filter for compatibility.

Change local_install.extensions.checkCompatibility to false by double clicking on it's current value of true.

You might have to do the same with extensions.checkCompatibility

You may have to re-start Firefox before you install User Agent Switcher and if it installs then re-start Firefox again.

---

### Post by liljoe76 on 2007-01-19
Mr Tech's Local Install
[https://addons.mozilla.org/firefox/421/]("https://addons.mozilla.org/firefox/421/")
"Temporarily enables XPI install preference to get local XPI's to install and then sets it back to previous state."
in other words install extensions that havent been updated. 
oh and dont forget your [FEBE and CLEO]("https://addons.mozilla.org/search.php?app=firefox&q=febe&cat=null&type=null&appfilter=null&platform=null&date=null&sort=newest&perpage=10")
absolute MUST haves!

ps good timing!!! ^^^^

---

### Post by szf on 2007-01-19
It's hard to walk the hard line - but if you feel you can argue and walk - ask the website  owner "WTF are you thinking with IE5.5+ only?!?!"

Satisfaction isn't likely, only hope that co.'s that enforce such policies end up in the elephant boneyard where they rightly belong.

---

### Post by ciscosurfer on 2007-01-19
> **in_flu_ence said:**
> Really appreciate all your help. fantastic to see replies within minutes. Nevertheless, the user agent thingy doesn't work with firefox 2.0.0.1

So i guess i have to wait till the thing is updated.I use the User Agent Switcher and I am running FF 2.0.0.1 :D

---

