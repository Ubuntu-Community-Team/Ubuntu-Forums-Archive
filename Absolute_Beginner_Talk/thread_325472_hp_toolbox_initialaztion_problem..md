---
title: "hp toolbox initialaztion problem."
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by photomaster106 on 2006-12-25
I have auto detected my hp deskjet3520 and have installed the model into the computer.It is Usb and was working properly when this was a windows machine.thinking maybe I had lost a usb connection i changed plugs,then cables then took my belkin router out of the loop.
The system autodetects the printer ,sends the test page,and even shows it printing but I get no output.
When i check in the console the printer is installed and the proper serial # is displayed.
When I try to open the hp toolkit to complete the install I get an error message that pyhton qt3 has not been installed and that the GUI will be termanated.Any suggestions??

---

### Post by Sef on 2006-12-25
> When I try to open the hp toolkit to complete the install I get an error message that pyhton qt3 has not been installed and that the GUI will be termanated.Any suggestions??

To install python qt3, open the terminal (Applications > Accessories > Terminal) and type

```
sudo aptitude update
```

```
sudo aptitude install python qt3
```

---

### Post by photomaster106 on 2006-12-25
Thank you i am pasting the readout from those instructions which if i read it right still says I do not have qt3 it reads as follows:


Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Fetched 4B in 26s (0B/s)
Reading package lists... Done
mmckinley@mmckinley:~$ sudo aptitude install python qt3
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find package "qt3".  However, the following
packages contain "qt3" in their name:
  qt3-assistant libqt3-java qt3-qtconfig libqt3-mt-mysql python2.4-sip-qt3
  python-sip-qt3 libqt3-jni python2.4-qt3-gl libqt4-qt3support qt3-linguist
  libqt3-i18n qt3-examples qt3-dev-tools libqt3-compat-headers
  libqt3-mt-odbc python-qt3-gl libavahi-qt3-dev python-sip4-qt3
  qt3-designer libavahi-qt3-1 libqt3-mt-dev qt3-apps-dev
  qt3-dev-tools-embedded libqt3-mt-sqlite libqt3-headers libqt3-mt-psql
  qt3-doc qt3-dev-tools-compat python2.3-sip-qt3 libqt3-mt
  gcin-qt3-immodule
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
mmckinley@mmckinley:~$

Wiil any portion of this get me where I need to go??

---

### Post by photomaster106 on 2006-12-26
I am not trying to be a pest,i can see that there are many others having problems with this distro,but i have been working on several issues for quite some time now and really need some help.

I have entered the output aboyut searching for python qt3 and it seems that it is not installed on my computer.
Since the hp toolkit will not work without it is there another source for this file that a newbie like me can install and solve this problem?? or is there another command that wiil find it on my machine.

Please look at the output on my previous post.

---

### Post by photomaster106 on 2006-12-27
I seem to have fixed the problem,I do not know how i did it but my printer is working and I am not going to look a gift horse in the mouth i am simply going to accept my good fortune.//

Thread closed

---

### Post by matchstich on 2006-12-27
mine say i need  press  F6 or go to device refresh all  during or after installation.  mine was installed using the add a printer and it works. so, i am not sure what to do here.

---

### Post by nu2this on 2007-01-19
For those trying to find that python qt3: the reason you can't get it is a simple typo You need to enter python-qt3 that hyphen is important. 
There is also another way to install python-qt3 System>Synaptic click Search type in python-qt3 in the box. Then mark for install, click apply done!

---

