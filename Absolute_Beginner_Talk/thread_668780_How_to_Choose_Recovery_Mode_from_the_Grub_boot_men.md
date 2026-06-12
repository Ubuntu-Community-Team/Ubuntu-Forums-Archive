---
title: "How to Choose Recovery Mode from the Grub boot menu from installation CD?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-01-15
I have a lenovo t61p thinkpad with nVidia Corporation Quadro FX 570M graphics card. The installer fails to create a usable xorg.conf file and the system reboots into an unusable black screen as x refuses to start. I read that this is caused by the installer selecting the nv driver, which does not support this card.

At the following link: [http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)
It says that to fix this you have to reboot into rescue mode and hand-edit xorg.conf to use vesa driver until the restricted nvidia driver is enabled.

How do I  Choose Recovery Mode from the Grub boot menu when attempting to install Ubuntu from the CD?

---

### Post by original_jamingrit on 2008-01-15
Sorry, there must be some misunderstanding.  You need to install Ubuntu before you have a GRUB menu to access.

In the howto, it says to wait after x tries and fails to start while on the livecd.  The livecd will, after several minutes, boot into "safe graphics" mode, and then you will be able to install.  Once you've finished installing, you will reboot and _then_ see the GRUB menu.

---

### Post by MountainX on 2008-01-15
Thanks for your reply. I cannot get the live CD to boot at all.

I'm trying safe graphics mode on the "alternate CD" (Ubuntu 7.10) and it has been stuck at the blank screen for more than an hour. I know one needs to be patient, but if it hasn't booted in an hour I'll be surprised if it will boot no matter how long I wait.

I'm trying to follow the info at this link:
[http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)

---

### Post by zvacet on 2008-01-16
Are yours CD O.K.?Did you chek [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and disc for errors?did you burn disc in low speed?If everythiing is O.K. you will install Ubuntu but you will have black screen,so after reboot you will select recovery mode and type 

```
dpkg-reconfigure xserver-xorg
```

When you come to the driver section select vesa and continue to the end.After restart you will have basic graphic and you will be able to search for your video card driver.It is in resricted driver manager.

---

### Post by MountainX on 2008-01-16
I posted my latest status here:
[http://ubuntuforums.org/showthread.php?p=4147414#post4147414](http://ubuntuforums.org/showthread.php?p=4147414#post4147414)

I am unable to get Ubuntu to install.

---

### Post by MountainX on 2008-01-16
Yes, my CD's are OK. I ran the CD verification on the live CD. I have burned about half a dozen CDs (live, alternate, 64bit, 32bit, server, etc.). 

I can get Ubuntu to install from the alternate CD. I can get a command prompt and I can edit xorg.conf. However, I can't get the X server to come up. I just get a blank screen.

---

### Post by zvacet on 2008-01-16
```
sudo /etc/init.d/gdm start
```

---

### Post by MountainX on 2008-01-16
the gdm tries to start and it fails.
I removed Ubuntu and installed PC-BSD. It works.

---

### Post by macogw on 2008-01-16
Try using the Alternate CD.  It uses a [text user interface](http://en.wikipedia.org/wiki/Text_user_interface) for the install.  If it still has the driver wrong after it's done installing, you can fix it through the recovery console that's in GRUB.

---

### Post by MountainX on 2008-01-16
I have already installed using the alternate CD (text install). I have gone into Grub and edited the driver (to vesa). I still cannot get X server to run, so I don't get any GUI. I only get a blank screen after booting up. PC-BSD will install and run at 1920x1200 with the vesa driver, so this is something specific to Ubuntu.

Here's the thread: [http://ubuntuforums.org/showthread.php?t=649609](http://ubuntuforums.org/showthread.php?t=649609)

---

