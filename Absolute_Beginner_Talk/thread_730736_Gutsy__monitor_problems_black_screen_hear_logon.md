---
title: "Gutsy / monitor problems black screen hear logon"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by sprintexec on 2008-03-21
I have trawled around a few of the earlier replies to people with this problem they don't fix it completely.

Here is where I'm at with it, when I start up my computer I can interrupt and go to recovery mode

I can then get into xconf and manually set up my monitor details, it is  Mitac MT-15EX6 though  I have had difficulty finding details about it re horz / vert  and refresh rates

When I do this and restart it works, but when I close down and then restart it goes 'back to black' what am I not doing or doing wrong? Thanks in advance, AJ :confused:

---

### Post by teaker1s on 2008-03-22
have you tried in recovery mode
```
sudo dpkg-reconfigure xserver-xorg
``` and worked thru the options to detect video hardware and basic resolution settings

---

### Post by sprintexec on 2008-03-22
> **teaker1s said:**
> have you tried in recovery mode
```
sudo dpkg-reconfigure xserver-xorg
``` and worked thru the options to detect video hardware and basic resolution settings
yep have been thru this and managed to get everything back up and running, then closed down and started up again to find i'd lost it all. so by a process of trail and error got it back again, thought i'd managed to save it as my primary source, for want of a better description and you guessed it lost it all again. is there something really basic i'm missing (like a brain) ? tks for yr help AJ

---

