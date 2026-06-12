---
title: "How to set up ubuntu 8.10 on MBP 4,1 properly?"
date: 2009-01-14
forum: Apple Hardware Users
---

### Post by HanDuo on 2009-01-14
Hi,

I have installed ubuntu 8.10 intrepid on my MacBookPro4,1. After installing the main system, I tried to set up additional stuff according to the instructions from this wiki:

[https://help.ubuntu.com/community/MacBookPro4-1/Intrepid]("https://help.ubuntu.com/community/MacBookPro4-1/Intrepid")

1st problem: The adjustment of the LCD backlight does not work out of the box. 
Furthermore: when I try to follow the instructions from the wiki (install stuff via the terminal) I get the message that the packages/files can not be found. This happens with every package I want to install via shell command.

2nd: I've set my keyboard-layout to MacBookPro an got this message (get this message every time I start the system): 

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10502000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

When it comes to Linux I am kind of a greenhorn, so I really don't know how to go on? Where can I get the needed packages/files and how can I set up the keyboard-layout properly?

Any proposal?

Thank you for helping me.

HanDuo

---

### Post by cyberdork33 on 2009-01-14
If those packages are not being found, it is likely because you have not added the mactel sources properly:
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

The keyboard thing is a bug I think and is currently getting a lot of attention. It might be best to just change it back to what it was for the time being.

---

