---
title: "Blank screen on imac 27'' i7"
date: 2010-05-16
forum: Apple Hardware Users
---

### Post by coucou2 on 2010-05-16
I have an imac 27'' i7 and cannot get to install ubuntu.

I always get a blank black screen when during installation even when I select the "safe graphic mode". During installation, the i get some multi-colored straits at some point and then nothing, it returns to the black screen.

I even tried to partition my hard drive with Gparted and got the same blank black screen even with the "safe graphic mode" option.

Have you encountered such a problem?

---

### Post by byStanderone on 2010-05-16
...you got the -64 version of the installer? just want to know.

---

### Post by coucou2 on 2010-05-16
Yes, I got the 64 bit version. I tried 10.04 and 9.10 and got the same issue.

---

### Post by byStanderone on 2010-05-16
...came across this workaround, hope it helps"
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by coucou2 on 2010-05-16
This still didn't work for me. I used the "nomodeset" at F6; but I still the blank screen at Install, right after the ubuntu logo

---

### Post by B_Free on 2010-05-16
Try this post
[http://ubuntuforums.org/showthread.php?t=1438243&page=5](http://ubuntuforums.org/showthread.php?t=1438243&page=5)
Go to oswaldkelso site for a lot of info especially about the iMac. Pay more attention to postings #44 and #45.

---

### Post by lemmof on 2010-05-16
I'm having the same issue with my machine.  The only difference is that I have an i5.  The screen is just black after the first menu.  I tried checking the "nomodeset" but that didn't help.  My graphics card is an ATI Radeon HD 4850 which is supposedly supported.  Certainly an iMac isn't exotic hardware?

> **B_Free said:**
> Try this post
[http://ubuntuforums.org/showthread.php?t=1438243&page=5](http://ubuntuforums.org/showthread.php?t=1438243&page=5)
Go to oswaldkelso site for a lot of info especially about the iMac. Pay more attention to postings #44 and #45.

I don't see anything there that helps me at all.  Maybe I just don't get it.

---

### Post by linuxopjemac on 2010-05-17
Oswalds' site is for PPC iMacs...

---

### Post by coucou2 on 2010-05-24
Any idea on why I cant get to install Lucid on my imac 27'' i7. Even using the F6 "nomodeset" option, I still get a black screen during the installation process. Please help!!!

---

### Post by linuxopjemac on 2010-05-24
[http://www.technicaljar.com/?p=267](http://www.technicaljar.com/?p=267)

See if that works for you, let us know. Remember to install the propietary video driver FGLRX after installing ubuntu to get full video performance

---

### Post by coucou2 on 2010-05-24
Thanks, but I tried 9.10 but gets the same issue of black screen. Sorry

---

### Post by lemmof on 2010-05-24
> **linuxopjemac said:**
> [http://www.technicaljar.com/?p=267](http://www.technicaljar.com/?p=267)

See if that works for you, let us know. Remember to install the propietary video driver FGLRX after installing ubuntu to get full video performance

This doesn't help because 10.04 doesn't have a "Safe graphics mode" option.

---

### Post by xygon on 2010-05-27
This is what worked for me, to do this you need a working internet connection and a another computer connected to the same network as the iMac.
I installed ubuntu through Bootcamp / Windows / Wubi, but I guess that doesn`t matter.

[LIST=1]
[*]Start Ubuntu-installation ([installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") for Bootcamp/Windows)
[*]When rebooting into ubuntu for the first time, keep your patience and let the installation finish with a black screen (took about 5 min). The installation should reboot automatically when it is done.
[*]On the second reboot, boot normally into Ubuntu and wait while Ubuntu is loaded with a blank screen.
[*]After a while(a least 1 min), press CTRL+ALT+F1. This will give you a command line you wont see...
[*]Here comes a tricky part: with a blank screen enter the following lines(change 'username' and 'password' with your actual username/password).
[LIST]
```
username
password
sudo apt-get install openssh-server
password
```
[/LIST]
[*]These commands will download(304kB) and install a ssh-server. After typing your password for the second time you should be able to access your computer via ssh from another computer. To find the IP-adress of your ubuntu-install try to "ping ubuntu" which is the default computername if installing by Wubi or you can try to check your router log.
[*]If you are successfully in logging into ssh from another computer you are no longer blindfolded and can continue to download and install the graphics driver(94MB) you need from the other computer:
[LIST]
```
wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run)
sudo sh ati-driver-installer-10-4-x86.x86_64.run
sudo /usr/bin/aticonfig --initial
sudo reboot

```[/LIST]
[*]You should now be able to start your ubuntu-installation normally.
[/LIST]

---

### Post by coucou2 on 2010-05-28
ok, i have now manage to install kubuntu 9,10 from the alternate CD, but I still have a couple of problems:

1. the system doesn't boot after the install is completed. I can see the linux logo when refit starts, but it doesnt boot into ubuntu. Grub is installed in the same partition were ubuntu is and the installation. Any idea?

2. During the installation process, my ethernet network is not detected and therefore I don't have internet connection. Have you encountered such problems?

Thanks

---

