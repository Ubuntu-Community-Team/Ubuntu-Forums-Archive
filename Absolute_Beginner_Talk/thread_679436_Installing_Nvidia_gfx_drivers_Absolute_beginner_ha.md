---
title: "Installing Nvidia gfx drivers? Absolute beginner have no idea!"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by livewire3030 on 2008-01-27
Hello, 

For the last couple of days now ive been trying to install my nvidia gfx drivers. There doesn’t seem to be an idiots guide on how to do this or anything that really explains the process for installing anything or explaining how to do anything for that matter. I have been on the mirc ubuntu channel, and its almost impossible to get someone to really explain it all in complete n00b talk.

Anyways,  I have a dell d630 with a nvidia quadro nvs 135m.. I have downloaded the latest 64 bit linux drivers from the nvidia site and tried following the instructions on how to install them by going to "Terminal" and typing "sh NVIDIA-Linux-x86_64-96.43.01-pkg2.run" .. Every time I do this it complains that i have to do it from Root?? i have no idea what this root is.. But i searched up on google and apparently you have to type in "SU" to get to root. when i type in SU it asks me to enter my password which i do, but it doesn’t like it, says authentication failure and sorry. So i have no idea why the password i use to log into ubuntu wont work in the terminal. So that process wont work.. 

The people on mirc said to use the Restricted drivers manager page from the system --> admin tab and to click the checkbox to enable the driver. Apparently this is a much easier way of doing it. I have tried this and that wont work either.. says i need the package "nvidia-glx-new".. What is this?? How do i get this? 

I am totally new to linux.. i'm trying to convert from windows and trying learn new things about this linux but am coming to the point where its just too hard and confusing. Everything is a complete mission and hassel.. Everything help wise on the net is filled with so much jargon and pre-assumed knowledge.. Is there some complete idiots guide to everything linux related?? anything that explains what linux is all about why its differnet to windows what all these kernel, envy,  root stuff is? why you cant just double click things to install etc etc and why there seems to be so many random applications to installing stuff. It's all to overwhelming for new people to jump on board the linux ship .   Can someone please help me?  :confused::-(

---

### Post by emarkd on 2008-01-27
1.  When you need root in Ubuntu, use sudo instead of su

2.  You can install any package by running:

```
sudo apt-get install packagename

```
where packagename is the name of the package.

See [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) for some good information on installing things in Ubuntu

---

### Post by swoll1980 on 2008-01-27
[http://ubuntuforums.org/showthread.php?t=679424](http://ubuntuforums.org/showthread.php?t=679424)

---

### Post by FuturePilot on 2008-01-27
Try going System>Administration>Software Sources. Check all the boxes in the first tab and uncheck the CD-ROM if it happens to be checked. Go to the Updates tab and check the first two boxes and optionally the fourth. Hit Close and Reload the sources when prompted. Then try the Restricted Driver Manager again.

---

### Post by mikewhatever on 2008-01-27
> **livewire3030 said:**
> Hello, 

For the last couple of days now ive been trying to install my nvidia gfx drivers. There doesn&#8217;t seem to be an idiots guide on how to do this or anything that really explains the process for installing anything or explaining how to do anything for that matter. I have been on the mirc ubuntu channel, and its almost impossible to get someone to really explain it all in complete n00b talk.

Anyways,  I have a dell d630 with a nvidia quadro nvs 135m.. I have downloaded the latest 64 bit linux drivers from the nvidia site and tried following the instructions on how to install them by going to "Terminal" and typing "sh NVIDIA-Linux-x86_64-96.43.01-pkg2.run" .. Every time I do this it complains that i have to do it from Root?? i have no idea what this root is.. But i searched up on google and apparently you have to type in "SU" to get to root. when i type in SU it asks me to enter my password which i do, but it doesn&#8217;t like it, says authentication failure and sorry. So i have no idea why the password i use to log into ubuntu wont work in the terminal. So that process wont work.. 

Try logging into recovery mode, the second option on GRUB screen. In recovery mod, you get admin privileges automatically, so don't need to worry about sudo or passwords.

> The people on mirc said to use the Restricted drivers manager page from the system --> admin tab and to click the checkbox to enable the driver. Apparently this is a much easier way of doing it. I have tried this and that wont work either.. says i need the package "nvidia-glx-new".. What is this?? How do i get this?

Had you taken a minute to run a google search, it would have led you to this link --> [http://packages.ubuntu.com/feisty/misc/nvidia-glx-new](http://packages.ubuntu.com/feisty/misc/nvidia-glx-new).
The restricted driver tool downloads and installs the driver for you, but, obviously needs internet connection.

> I am totally new to linux.. i'm trying to convert from windows and trying learn new things about this linux but am coming to the point where its just too hard and confusing. Everything is a complete mission and hassel.. Everything help wise on the net is filled with so much jargon and pre-assumed knowledge.. Is there some complete idiots guide to everything linux related?? anything that explains what linux is all about why its differnet to windows what all these kernel, envy,  root stuff is? why you cant just double click things to install etc etc and why there seems to be so many random applications to installing stuff. It's all to overwhelming for new people to jump on board the linux ship .   Can someone please help me?  :confused::-(

Linux world is very diverse. You are expected to do some homework, get familiar with terminology and not to think Ubuntu is a free version of Windows. Linux is different, so there are different ways of doing things, which might seem confusing in the beginning.

Recommended reading:
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by livewire3030 on 2008-01-27
thanks guys for your help. much appreciated!

---

