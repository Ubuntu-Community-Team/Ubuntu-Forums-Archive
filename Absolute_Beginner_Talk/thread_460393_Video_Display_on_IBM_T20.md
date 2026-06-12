---
title: "Video Display on IBM T20"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by psistorm on 2007-05-31
First, let me say that this is my first time using Ubuntu, and that I'm a total newbie to the OS.  I just finished install Ubuntu Desktop 7.04 successfully on my IBM T20 Laptop.  Everything looks fine, except the video display seems limited to on 800x600 even though it supports 1024x768.  Can someone help me fix this problem?  I've checked the screen resolution setting and 800x600 is the max resolution available.  

I've looked at a few post like the following but I couldn't find the xorg.conf find to make the changes.
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20)

Any help would greatly be appreciated.

Thanks!

---

### Post by lazyart on 2007-05-31
it's located in /etc/X11/xorg.conf

I say do```
sudo dpkg-reconfigure xserver-xorg
```

Accept everything as-is, except when you get to the resolutions, manually add on 1024x768 and you're golden.

---

### Post by psistorm on 2007-05-31
thanks for your help.  i had to try it a few times but i got it working.

---

