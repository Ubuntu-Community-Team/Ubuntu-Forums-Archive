---
title: "Can someone tell me what this means? Thanks"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2006-05-05
I was trying to install a .deb file to try out the new opera browser and got the following: "**Could not open [B]*opera_8.54-20060330.6-shared-qt_en_etch_i386.deb*** Archive not supported[/B]"

I don't really understand why, deb files have been installed before, no problem.

thank you,

---

### Post by Sef on 2006-05-05
> I was trying to install a .deb file to try out the new opera browser and got the following: "Could not open opera_8.54-20060330.6-shared-qt_en_etch_i386.deb Archive not supported"

You were not opening it the correct way I believe.

First what version of Ubuntu are you running?

1) Dapper: simply click on the icon and up will pop a box that you click install on to install it.

2) Breezy: Applications > Accessories > Terminal

change to the where the package is:  For example, mine would be on the Desktop

cd ~/Desktop 

then

sudo dpkg -i name_of_package

If you start the name, you should be able to hit tab and the full name will come up.

For more info on installing:  

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

[http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")

---

### Post by Il_Tuo_Nome on 2006-05-05
Sef,

thanks for responding I thought maybe you were correct that I was opening it incorrectly. However, once I was able to save it to my Desktop I ran that command and got the following in the terminal:

> rosso@StuCazz:~/Desktop$ sudo dpkg -i opera_8.54-20060330.6-shared-qt_en_etch_i386.deb
Password:
Selecting previously deselected package opera.
(Reading database ... 67922 files and directories currently installed.)
Unpacking opera (from opera_8.54-20060330.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera


The packages it says aren't installed, are those part of the deb file or do I need to install them in order to continue?

thanks again

---

### Post by Sef on 2006-05-05
You need to install them in order to download Opera.   Have you enabled multiverse and universe?

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by Il_Tuo_Nome on 2006-05-05
After my last post it wanted me to update. In the terminal I had to run ***sudo apt-get install -f***. I'm assuming that took care of enabling multiverse and universe, because it installed after that.

Thank you for all your help :)

---

### Post by Sef on 2006-05-05
> I had to run sudo apt-get install -f.

That just gets the dependencies.  You should enable multiverse and universe, if they are not enabled.

---

### Post by patrick295767 on 2006-05-05
To install full set of webbrowsers + opera via patrick's script: 
  
sudo su
chmod +x webbrowsers.sh
./ webbrowsers.sh
```

#!/bin/bash
### webbrowsers, ...
##

######## installing qt3
apt-get -f -y install qt3-dev-tools
apt-get -f -y install qt3-apps-dev
apt-get -f -y install libqt3-headers
apt-get -f -y install qca-dev
apt-get -f -y install libqt3c102-mt
export QTDIR=/usr/share/qt3

##########end ###### make install !! ##############"


mkdir /root
mkdir /root/miniram
apt-get -f -y install galeon
apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install elinks
apt-get -f -y install
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install mozilla
apt-get -f -y install sylpheed
apt-get -f -y install mozilla-firefox
apt-get -f -y install sun-j2re1.5 flashplayer-mozilla
apt-get -f -y install mozplugger mozilla-browser
apt-get -f -y install opera
apt-get -f -y install mplayerplug-in
cd /root/miniram
wget http://patrick295767.sitesled.com/miniram/opera_8.54-20060330.6-shared-qt_en_etch_i386.deb
dpkg -i opera_8.54-20060330.6-shared-qt_en_etch_i386.deb
cd /root/miniram

```

---

