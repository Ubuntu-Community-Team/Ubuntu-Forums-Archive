---
title: "A Couple of Beginner Questions"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by davidajohnson12 on 2008-03-02
Hello Everyone,

I am a linux newbie. I have looked at it for a while, but am just now really trying to use it. I would potentially like to like to have Linux be my primary OS, if not my only OS. However, after installing Ubuntu, I have a few questions that I was hoping someone would be kind enough to help me with. If anyone has time to reply, I would appreciate it. There is no need for one person to answer every question, unless you would like to. Thank you so much everyone.

Questions:

1.    Does linux work on a mac and pc?

2.    Is there an easy way to achieve my monitor's 1280x1024 resolution? Linux only gives me the option for 1024x768. Here is my situation:
        - I have a Compaq Presario SR1630NX, original specs with memory upgraded to 2GB.
        - I have a Samsung SyncMaster 730B monitor.
        - I have windows xp home installed with 10GB allotted to Ubuntu Studio.
            - Is Ubuntu Studio the problem? Should I just use Ubuntu? Kubunutu? ... ?

3.    Is Wine the best program for running windows apps? How well does it work? Are there any major apps that you know of that are not supported in Wine?


This is just a start. I am sure I will have more questions along the way, but if someone could help me with these, it would really give me a jump start. And, if anyone wants to add any other linux advice/information that may be helpful to me, I would appreciate it. Thanks again.

Dave

---

### Post by JoshuaRL on 2008-03-02
1).  Yes, it just uses a different version depending on what type of processor you have.

2).  Ubuntu Studio is most not likely not the problem.  Could you post your type of graphics card?

3).  Well, the best is if you can find an open-source alternative.  Many are better than the windows varients.  But if thats not an option, yes Wine is good.

[This is Wine.](http://www.winehq.org/)
[Why Wine is so important.](http://www.winehq.org/site/why)
[Wine myths debunked](http://www.winehq.org/site/myths)
[Wine Applications Database,](http://appdb.winehq.org/) where applications and their ability to be run with Wine are listed.

---

### Post by Tatty on 2008-03-02
1.  Newer Macs use Intel chips - you can install Ubuntu on these as far as i am aware.

2.  To get your monitor resolution correct you first need to:
a) make sure you are running the correct drivers for your card (check restricted drivers manager)
b) configure xorg.conf to let ubuntu know which resolutions you can use (there is a graphical way for this in one of the menus under System, but im not on my ubuntu PC atm so i cant check its name - monitor setup or something like that)
c) select the screen resolution you want under System->Preferences->Screen Resolution.

3. Wine is the cheapest method of running windows applications, as it costs nothing.  There are commercial versions of wine - Cedega (which focusses on gaming) and CrossOver (which focusses on Business apps).  Alternatively you could install windows as a virtual machine, so it runs "under" ubuntu.  But that requires you to have a windows licence key.

---

### Post by hammad1337 on 2008-03-02
1- Does linux work on mac and pc?
Yes
2- Try Linux Mint Daryna, it has the same system as Ubuntu Gutsy, so you can get all the support here. Also, it has many little things builtin that make your work of applying themes and changing resolution on the fly, easier. I dont know the package name, but you could install that same functionality on an ubuntu too. So if any body knows, please do tell.

3- Wine is the best option for running windows programs. Most everyday programs do run. Some have issues and most issues are program specific. Most games, especially the latest and shiny ones donot run in wine. some new software also doesnot run. But usually, u do have a linux substitute available.

---

