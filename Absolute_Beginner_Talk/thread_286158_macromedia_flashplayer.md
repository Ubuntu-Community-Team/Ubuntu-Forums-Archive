---
title: "macromedia flashplayer"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2006-10-27
I am trying to install the aforementioned but cannot.I have installed flashplugin-nonfree but this is not enough when visiting various web sites Barclays.com for one there is a green icon which says download plugin when I click on this a box opens with Macrmedia Flash Player I click on download after about 10 mins it comes up Install failed do it manually.I did this and have got install_flash_player_7_linux.tar.gz on my desk top.I right clicked and it had the option to extract which I did and also have install_flash_player_7_linux on my desktop.Being new to all of this I dont really know what to do now.Any help would be appreciated.

---

### Post by aysiu on 2006-10-27
One of these should help you:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by lazyart on 2006-10-27
Is the site asking for Flash 8?  Flash 7 works, but there is no Flash 8 for Linux.  Version 9 is in beta.  This is a problem on ESPN as well... nothing really to do about it, unless you want to use WINE and IE/FF.

---

### Post by Fully216 on 2006-10-27
How you proceed depends on your system.  You can try to install the downloaded package, but I would first follow the guide found here, for Dapper.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Note: amd64 systems, there is no flash support (unless you try to get 32-bit working with linux32 package ~ somewhat complicated).  You should be able to get it up and running on i386 systems.

Since you have already installed flash-nonfree, did you setup your EDS environment?

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd 

Another option is to use automatix, which try to automate the installation of many non-free features in ubuntu, including flash.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Not sure if any of this applies if you have upgraded to the new version available yesterday, Edgy Eft.

---

### Post by SunnyRabbiera on 2006-10-27
Yeh this is not a flaw in linux or ubuntu, but a flaw in adobe.
You can try the flash 9 beta here though:
[try it]("http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz")

remember that this is a beta though

---

