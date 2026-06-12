---
title: "Really choppy scrolling"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Wizzy on 2007-02-14
I just installed the latest version of Ubuntu, and while it works pretty well - there's a problem with scrolling. I've got an Sapphire Radeon x1800xt - and when I scroll on a web page, or through a large list or something, it's very choppy. Like it's refreshing each time to show the new information or something. it's quite annoying, and I'm not sure what to do. I tried looking at some "help" thing, but it was way beyond me. Started talking about repositories, and this and that - and entering commands - but not saying where or anything like that. It was way beyond me.

---

### Post by igknighted on 2007-02-14
> **Wizzy said:**
> I just installed the latest version of Ubuntu, and while it works pretty well - there's a problem with scrolling. I've got an Sapphire Radeon x1800xt - and when I scroll on a web page, or through a large list or something, it's very choppy. Like it's refreshing each time to show the new information or something. it's quite annoying, and I'm not sure what to do. I tried looking at some "help" thing, but it was way beyond me. Started talking about repositories, and this and that - and entering commands - but not saying where or anything like that. It was way beyond me.

1) Install the drivers for your video card.  There are many how-tos on the site.  Personally I recommend just installing them from the repo's and then running aticonfig, it has never let me down.  To do this, enter these commands in the terminal:
```
sudo aptitude update
sudo aptitude install xorg-drivers-fglrx
sudo aticonfig --initial
```

2) Have you disabled ipv6?  There is an option to disable it systemwide which I don't know, but if you are using firefox try about:config, then search for ipv6.  Once you find an entry that says 'disable ipv6 false' double click it to change to true.  That should help scrolling on web pages.

---

### Post by maxamillion on 2007-02-14
Sounds like you just need the binary drivers ..... resources on ATI drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
[http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoATIRadeonX800](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoATIRadeonX800)

hope that helps

EDIT: I got beat to it.

---

### Post by Wizzy on 2007-02-14
Fixed! Thank you - that a much better run-through of it. Although, not all the commands worked - I had to skip all the "*.deb" steps, because it didn't understand them :) but I did what I could, and it worked.

---

### Post by FrancoNero on 2007-10-10
ipv6 can't be the issue, sicne scrolling is also a problem in other windows, not just firefox. moving and opening any windows is also very choppy on my system. i have the correct latest intel modesetting driver enabled, xorg, everything updated. even with compizfusion off, it's choppy. the system is fast, it's just the windows and the scrolling really. how can I fix that?

---

### Post by vlam21 on 2008-07-09
Sorry to bring up a dead topic, but I have an identical problem, but I'm using a Lenovo T61P with an nVidia 570M video card (with nVidia drivers). Could any of you recommend something? The scrolling is choppiest when I scroll down a page that has many pictures or videos.

---

### Post by Darkchef on 2008-07-09
It's choppy because of a graphics card driver problem , try to install the graphics drivers from synaptic by searching for Nvidia or ATI. This should solve the problem for you.

---

