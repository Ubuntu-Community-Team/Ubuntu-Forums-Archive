---
title: "[SOLVED] Nvidia problem with MacbookPro Santa Rosa (again!)"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by josiano on 2008-01-15
Hello.
Sorry to bother with this thread again but I've been reading the tons of topics about this and the santa-rosa-wiki but I am still stuck...

I have installed Gutsy on my macbook pro (santa rosa) and everything went well except the display...
After hours of trying to find out how to install the latest nvidia (binary) driver, I got it installed and all (I've enabled it in the Restricted Drivers) but it's still impossible to change the screen resolution (except to 800x600 or 640x480).
I also have the Nesa driver selected in my Screen and Graphics Preferences.
I should notice that I 1st tried to install nvidia-glx-new and had same results.
Many thanks for your advices.

_j

---

### Post by overdrank on 2008-01-16
> **josiano said:**
> Hello.
Sorry to bother with this thread again but I've been reading the tons of topics about this and the santa-rosa-wiki but I am still stuck...

I have installed Gutsy on my macbook pro (santa rosa) and everything went well except the display...
After hours of trying to find out how to install the latest nvidia (binary) driver, I got it installed and all (I've enabled it in the Restricted Drivers) but it's still impossible to change the screen resolution (except to 800x600 or 640x480).
I also have the Nesa driver selected in my Screen and Graphics Preferences.
I should notice that I 1st tried to install nvidia-glx-new and had same results.
Many thanks for your advices.

_j

Hi and if you have the restricted drivers installed you may just reconfigure your xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` And also you say Nesa  driver in the screen and graphics are you meaning vesa?

---

### Post by josiano on 2008-01-16
Hi.
So I reconfigured my xorg and it's still the same problem: no 1400x900 resolution possible.
(and of course I meant "Vesa" driver)
Could someone please explain me if it's possible to desinstall all nvidia graphic drivers and do it again from scratch (only for graphics) ?
Would it be a good solution ?

I am very confused right now because I followed exactly the wiki-macbookpro-santa-rosa,  I was  never given the advice on first reboot to choose nvidia-glx-new driver (as stated in wiki) and now it looks very hard for me to get it working.
Thanks again for your help.

_j

---

### Post by josiano on 2008-01-16
Ok I got it working thanx to nvidia-settings and nvidia-xconfig...
Sorry for the noise !
Cheers.

_j

---

### Post by josiano on 2008-01-16
I should have waited a bit more before saying it's solved as it is not.
After having my resolution perfectly displayed (1440x900), I rebooted, and now I'm back to 800x600...
I've found the thread about "keeping nvidia drivers on reboot" but nothing helped.
I uninstalled everything from nvidia, reinstalled nvidia-glx-new, I ran nvidia-xconfig, I restarted X and I am always back to the beginning... which is 800x600...
If I have a look at my xorg.conf file, it says "mode:1440x1440", which looks weird to me.

Anyone knows a workaround ?
It's been two days now that I try to have this nvidia driver working, without success.
I am very disappointed not to be able to use ubuntu now.
Best.

_j

ps: forgot to mention that I also have a "failed to initialise HAL" error on boot now.

---

### Post by overdrank on 2008-01-16
> **josiano said:**
> I should have waited a bit more before saying it's solved as it is not.
After having my resolution perfectly displayed (1440x900), I rebooted, and now I'm back to 800x600...
I've found the thread about "keeping nvidia drivers on reboot" but nothing helped.
I uninstalled everything from nvidia, reinstalled nvidia-glx-new, I ran nvidia-xconfig, I restarted X and I am always back to the beginning... which is 800x600...
If I have a look at my xorg.conf file, it says "mode:1440x1440", which looks weird to me.

Anyone knows a workaround ?
It's been two days now that I try to have this nvidia driver working, without success.
I am very disappointed not to be able to use ubuntu now.
Best.

_j

ps: forgot to mention that I also have a "failed to initialise HAL" error on boot now.

HI and are you using nvidia-settings to set your resolution, if so are you using this command ```
gksudo nvidia-settings
```

---

### Post by josiano on 2008-01-17
Yes, and when nvidia-settings opens I have :

"You don't appear to be using the Nvidia X driver.  Please edit your X configuration file (just run nvidia-xconfig as root), and restart the X server"

Which is what I do, and then I'm back in 800x600, etc...
I can't understand how it could have worked for a few minutes (with same commands).

Thanks for your help.

_j

---

### Post by josiano on 2008-01-21
I re-installed Ubuntu, but this time the i386 one.
It worked perfectly, I had the nvidia-glx-new working on 1st reboot. This is mentioned in the wiki but they say also "install i386 or amd64" and with amd64 version, it was a pita to get it working (I'm a n00b)...
Cheers.

_j

---

