---
title: "[SOLVED] compiz fusion problems with integrated geForce 6150"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by ohmycar on 2007-10-27
I just installed 7.10 on my brothers computer and I can not get it to enable the advanced desktop settings. He has a integrated geForce 6150 and the driver being used is the nv-Nvidia driver. 

I installed the "advanced desktop setting menu" already , but it won't let me enable them when I go to the visual effects tab in "Appearance"

The error it gives me is "Could not enable desktop effects" and that is all it says. Anyone know of a possible solution to this? or is the geForce  6150 not compatible with compiz-fusion

---

### Post by forestpixie on 2007-10-27
you need to have the nvidia driver - go to restricted driver manager - in admin - and enable the driver there

---

### Post by ohmycar on 2007-10-27
I did enable the driver and I am still getting the same error. When I enabled it , it installed the nvidia-glx new and I figured that would fix the problem, but I still can not apply the desktop effects.

---

### Post by ohmycar on 2007-10-27
Also, I am using a VGA cord to plug my computer into my lcd, if that makes a difference.

---

### Post by Mondoman on 2007-10-27
Check out this thread, especially what I ended up doing near the end of it.
[http://ubuntuforums.org/showthread.php?t=566765](http://ubuntuforums.org/showthread.php?t=566765)

---

### Post by ohmycar on 2007-10-27
So great news, I did these two commands

sudo apt-get install nvidia-xgl

 and sudo apt-get install xserver-xgl

and now my compiz fusion works , but I can not see my mouse cursor at all. I am navigating my screen by assuming where my mouse is, it is terrible. 

Anyone know how to make my mouse visible again?

---

### Post by ohmycar on 2007-10-27
So I also tried removing the xserver-xgl from synaptic package manager, and stil no luck with getting my cursor to show up. Anyone have any ideas/suggestions for this problem?

EDIT: Rebooted comp, and cursor showed up. seems before I was only rebooting x-server.

---

