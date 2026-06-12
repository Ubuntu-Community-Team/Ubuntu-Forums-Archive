---
title: "How to reinstall/revert graphics settings from command line"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by neodorian on 2007-08-28
I installed Ubuntu on my Toshiba Portege M200 tablet via Wubi (since the tablet has no CD drive).  It was working OK but I enabled desktop effects to see how they would play out on my laptop.  I got Compiz and all that working but shortly thereafter I got the black window bug and figured it just wasn't gonna work on my setup (beta software and all...) I unchecked the desktop effects but was still having issues with the desktop staying all black and not being able to completely get to the desktop.  I went to restricted drivers manager and unchecked the option to use nvidia driver.  It then removed nvidia-glx and I rebooted.  Now I can't even get the desktop to respond when I log in.  I see it for a second sometimes when I restart X but I can't manipulate anything through the GUI.  I can ctrl-alt-f2 and get to the command line but I wasn't sure where to start to repair things or revert them back to the non-restricted driver.

---

### Post by dstew on 2007-08-28
You probably need to reconfigure the X server. To do this, boot into recovery mode, and issue the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

Answer the questions the best you can, then try **startx**

---

### Post by neodorian on 2007-08-28
Alright.  I did that but when I start X, I still have everything covered by a white screen.  I know my desktop is still there because if I click around whree the icons are, I see the computer is busy and the mouse pointer chages to show something is firing up.  When it hit ctrl-alt-backspace to restart x, I see the desktop wallpaper for a second before it starts over again.

This isn't pressing as it's a dual boot that I'm using to play with.  Normally in a situation like this I would just reinstall but the whole point of me playing with this is to learn to troubleshoot it the way I would be able to if it were Windows.

---

### Post by bodhi.zazen on 2007-08-28
If that did not work, what videocard are you using ? And what have you done up to this point ?

It sounds as if your card needs to be configured for copmiz and I assume you are getting a white screen because you set copmiz to the default.

Also post your xorg.conf

---

### Post by neodorian on 2007-08-28
It's a Geforce Go 5200 and disabling compiz and then telling it not to use the restricted driver was what started this.  Once I figure out how to get a copy of my xorg.conf I'll be glad to post it, but I'm booted into XP on the same computer now.

I had really just installed Ubuntu Feisty via Wubi, did all the updates, and then enabled the restricted nvidia driver.  It worked OK and I've used the nvidia-glx driver plenty of times on this laptop.  It was once I disabled a buggy compiz that I got this issue.  I may just reinstall but then I won't learn anything.

---

### Post by staid on 2007-11-17
This thread's pretty old now, but I found it while trying to trouble a very similar problem with Ubuntu 7.10 and my gforce 5200fx.  After the install, I tried to set up dual-monitors.  The setting was easy to find, but when I logged out, all graphics was shot.

So I logged into recovery and tried what dstew said:
> sudo dpkg-reconfigure xserver-xorg
but what actually worked for me was:

> sudo dpkg-reconfigure -phigh xserver-xorg

I'm still a noob but I found another tip to try to edit  the /etc/X11/xorg.conf file so I typed > vi  /etc/X11/xorg.conf at the command line and saw at the top of the file that you could restore graphics changes to the xorg.conf file with the same command, just with the -phigh switch added.

Anyway,
Thanks,

staid

PS.  you need to type  ctrl+z   to get out of a vi session

---

