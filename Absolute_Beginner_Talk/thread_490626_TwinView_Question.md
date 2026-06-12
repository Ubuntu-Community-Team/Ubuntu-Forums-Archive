---
title: "TwinView Question"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Betta on 2007-07-02
Hey there, I finally got TwinView to work, it works quite well, however, my two monitors are of different resolution and the VGA one shows up as the main monitor even though it's plugged into the secondary port. I have a DVI Widescreen Monitor (1440x900), and a VGA regular monitor (1280x1024). The resolution shows up as 2720x1024, which is good except the "bottom" on the widescreen is cut off. Is there any way to fix this? Also, I'd like the login screen to be on the widescreen not the VGA, for some reason it always thinks the VGA one is the main one, don't know why. This isn't as important as my first question though, so if you don't know a way off the top of your head, don't spend too much time thinking about it. 

-Betta

P.S. is there a way to have separate backgrounds on each monitor?

---

### Post by Rocket2DMn on 2007-07-02
I don't think there is a way to fix that, it's just how twinview works - it shows your desktop as extra wide and covering two displays.
The configuration for which monitor is the primary and which is the secondary should be in your /etc/X11/xorg.conf file.  If you choose to edit this (with sudo of course), be sure to make a backup first.

---

