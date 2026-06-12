---
title: "adding programs to the applications menu"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by zionvier on 2007-11-25
Hey guys, first I want to thank those here that answer all the questions.  I've been using Ubuntu for over 6 months and this forum has been a life saver numerous times.  I'm not new to the Linux world though.

Anyway, I did the normal search for this and haven't found it like I have on other issues.

So how do I manually add to the applications menu?  I installed the Eclipse Web Tools Platform (something I think should be considered for a future release as an available Add/Remove applications option).  

But I'd like to add it to the applications menu manually.  Can someone point me in the right direction?  Is it a directory structure somewhere or an editable file?

---

### Post by road_rage on 2007-11-25
To Create a menu item, say for the application Prism, I found the steps below either on their www site or in the install notes or somewhere. All I am saying is that this is not because of my brain, but it definitely worked. 

sudo gedit /usr/share/applications/prism.desktop

Then add:

[Desktop Entry]
Encoding=UTF-8
Name=Prism
Comment=Prism
Exec=/opt/prism/prism
Icon=/opt/prism/chrome/icons/default/webrunner48.png
Terminal=false
Type=Application
Categories=Application;Network;
StartupNotify=true

Hope this helps. 

--RR

---

### Post by Xavieran on 2007-11-25
There is an easy GUI way which I find much quicker...
Right click on applications and choose edit menu,then select the area you want to add an app to ,say in programming then click add item (could be a different word) then type the command and etc .

---

### Post by zionvier on 2007-11-25
thanks for the quick answers.  Between the two posts I was able to see the backend workings of the menus as well as the standard GUI to do it easily.  I suppose most people that go to Linux knowing how it works is often half of what we want to know.

To the moderators... you can mark this as solved/answered

---

