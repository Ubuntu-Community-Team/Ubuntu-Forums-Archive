---
title: "Setting up Internet help please"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by DSgamer692 on 2007-07-01
I've seen what linux can do over a regular operating system so I decided to try it out. I installed Ubuntu on top my laptop. My only problem now is that I can't get on the internet! I did go to the help pages and my wireless card was not listed. Not only that, but my card did not even turn on. With XP my card turns on automatically, with Ubuntu no lights go on. I have a Belkin wireless card and the model number is F5D8010. Thanks to those who attempt to help me!:p

PS: I see on Youtube all the time those nice look flashy effects, anyone wanna point me in the right direction on where to get that stuff? I think its called Beryl or something like that. Thanks guys!:D

PSS: I forgot to mention I did try using a wired connection as well and it did not work. I am on a LAN and all my computers work simplay by plugging in the cable, not with Ubuntu. Is there a driver or something I must install? Ok thanks again.

---

### Post by speaker219 on 2007-07-01
[http://ubuntuforums.org/showthread.php?t=259037](http://ubuntuforums.org/showthread.php?t=259037)

---

### Post by DSgamer692 on 2007-07-01
lol I'm sorry, but I'm new at this stuff. I am having trouble just installing this program:( I put the  ndiswrapper and the actual driver of my wireless card from belkin's site on a cd. Then I went on Linux and I extracted the program onto the desktop and I put the driver on the desktop... I'm confused on just how to install it:( Instead of a regular setup there are instructions. I DONT KNOW WHAT A KERNEL IS!:( Sorry if I'm being an annoying idiot (which I know I am), but I'm just having so much trouble getting my internet working that I dont know if its really worth trying to get Linux working correctly on my laptop

---

### Post by Raineer on 2007-07-01
There's not enough information to REALLY help you out, but assuming that one of those files has a **.deb** extension, you can run

```
sudo dpkg -i ndiswrapper.deb
```

Again, assuming that is a .deb file (a preset "package" file ready to install into a Debian distribution, like Ubuntu)

---

### Post by justinmiller87 on 2008-03-02
Are you still having trouble? I have a step-by-step installation guide in my signature for the F5d8010. It's the Airgo link.

---

