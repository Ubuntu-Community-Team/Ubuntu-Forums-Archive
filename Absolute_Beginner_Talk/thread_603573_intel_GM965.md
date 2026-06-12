---
title: "intel GM965"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by syncmasta on 2007-11-05
I decided to dedicate my new laptop to ubuntu as well as backtrack 2. Let me tell you something, running linux after a lifetime with windows feels like running away from your parents to join the circus act as an acrobat! 

 :lolflag:

Problem is, like running away from the safety and comfort provided by your parents, running ubuntu (at least for me now) feels very risky. I don't know of any fallback plans save for CTRL ALT BACKSPACE when everything goes wrong. I am facing these two problems. 

1. What can I do if I somehow screwed up my graphics driver installation? Or any driver installation for that matter? my laptop, a compaq presario V3658TU is running on the Intel GM965 chipset with X3100. 

I found this website 

[www.intellinuxgraphics.com](www.intellinuxgraphics.com) 

It shows that u can download some stuff, compile them and then just make install . Everything should be a -ok by then. Problem is one or two files failed to be found during the make file process or something and now it feels like I have screwed up the installation. :confused: 

2. Say if now I had installed ubuntu and have one more partition (free space) for a second intended distro, such as backtrack 2, How should I know what to add in grub for a dual boot? And which grub will that be? Because from my understanding is that each partition has their own /boot directory in their respective partition, where each /boot have their grub and menu.lst? 

I'm lost. Help me find my way gurus. This is my third reinstall of ubuntu, its now "scanning the mirror" as I type this on a desktop pc. :confused:

---

### Post by Inxsible on 2007-11-05
if you know that you have screwed up your graphics you can do this:
1) Backup the current xorg.conf file by```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```2)Revert your xorg.conf to the default ubuntu installation -- after which you will have to re-enable your restricted drivers if you use any.```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jordanmthomas on 2007-11-05
For what it's worth, you do not have to get the drivers for intel card as they are open source and are preinstalled for you.

---

### Post by syncmasta on 2007-11-05
much thanks. Your words of wisdom shall be saved in a text file inside my thumbdrive under the "OH **** WHAT SHOULD I DO NOW?" label. 

Now if I can only figure out how to successfully dual boot backtrack with ubuntu. That would be just great. The forum at remote exploit is far less helpful. (I use, or rather, learning to use backtrack for my computer security subject class)

---

