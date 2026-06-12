---
title: "Weird Problems"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-16
So I left my computer running for a while,  I came back 2 hours later and the wireless wouldn't reconnect. I couldn't open a terminal... I even used CNTRL+ALT+F1 to switch to virtual terminal and typed:
```

sudo reboot
&
sudo shutdown now

```
and nothing happened.

When I did a hard reboot (pulled the battery out of my laptop). It rebooted but the theme went back to the older 6.1 theme and a window about the Gnome loading problems came up.

Does anybody know what is going on here?  This has actually happened quite a few times and it is driving me crazy!

---

### Post by finer recliner on 2008-03-16
next time try a couple other things before doing a hard reboot:

restart X:
```
ctrl + alt + backspace
```

see what is hogging resouces:
```

ctrl + alt +f1
top
//take note of any resource hogging a ton of memory or CPU
//if you think its safe to stop the bad process, take note of it's PID and run:
kill <PID>

```

soft restart the kernel:
[http://www.arsgeek.com/?p=787](http://www.arsgeek.com/?p=787)

---

### Post by Victormd on 2008-03-16
> **neurostu said:**
> When I did a hard reboot (pulled the battery out of my laptop). It rebooted but the theme went back to the older 6.1 theme and a window about the Gnome loading problems came up.

If you need to "hard reboot," don't pull out the battery, just hold the power button for ~4 sec. and it should shut down... :)

as for the other problems, what's your graphics card? ATIs and Intels are known to have issues with Ubuntu... Also, this could be related to the hibernate/suspend modes that are not working properly. I saw a link somewhere that talked about it... I'm going to try to find it and I'll post it here for you...

---

### Post by Victormd on 2008-03-16
Here's the deal, I found this for HP laptops but I used it on a Dell and an HP and it worked for both:
"**Suspend/Hibernate**
Supposedly adding "nosmp" as a boot option, disabling Sync To Vblank in Beryl, and if you edit the /etc/default/acpi-support and set POST_VIDEO=false, suspend and hibernate
should work better. QUESTION: Is "nosmp" the option that makes this work? Anyone know?"

Source:[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

Hope these help...

---

### Post by neurostu on 2008-03-17
So I have a t61 and i have suspend working properly but not hibernate.  I also have an nvidia card with the restricted drivers installed.

What is really weired is I can leave my laptop for an hour or two and I come back and its already acting funky, other times I can leave it for hours and hours and I never get the problem.

---

### Post by Victormd on 2008-03-17
I observed a similar behavior on my wife's laptop (HP) where suspend would work sometimes but not consistant, that's why I think your problem might be related. After running the above, the problem stoped. Also, "laptop mode" is disabled by default on Ubuntu so if you haven't done so, you might want to turn it on and see if that helps.
Open a terminal and type:
```
sudo gedit /etc/default/acpi-support
```
At the bottom of the file, there is the ENABLE_LAPTOP_MODE variable, set this equal to true. A restart is required to enable this setting.
Read through this file to see some of the other options.

Other power applications can be found in the Extra Repositories. To install them, open Synaptic and install the following packages:
laptop-mode
laptop-mode-tools
laptop-detect
cpufreqd
cpufrequtils

> Source:[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

