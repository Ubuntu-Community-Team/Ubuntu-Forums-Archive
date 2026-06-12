---
title: "Screen resolution problem"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by hawkmooth on 2006-10-30
Hi there.

I've just installed Edgy Eft. And everything works, except the screen resolution. In the 'System -> Preferences -> Screen resolution' tool i can only choose 1024x768, but the DELL X1 runs 1280x768. I googled around and people referred to /etc/X11/xorg.conf, but my xorg.conf says 1280x768.

Does anyone know how to get ubuntu to run 1280x768?

Regards, Jeppe

---

### Post by bruce89 on 2006-10-30
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ahaslam on 2006-10-30
Are you running the generic 'vesa' driver? Should be mentioned in that file people keep referring to ;)

Tony.

---

### Post by hawkmooth on 2006-10-30
I used the debian reconfigure tool and switched to vesa with a 1280x768 resolution.

In 'System -> Preferences -> Screen resolution' I have 3 options. 640x480, 800x600 and 1024x768.

In the xorg.config there is 4 different modes:
SubSection "Display"
	Depth		24
	Modes		"1280x768" "1024x768" "800x600" "640x480"
EndSubSection

I don't get it... :confused: 

Why can't i choose from the all the resolutions in xorg.conf?

---

### Post by CatKiller on 2006-10-30
You may want to try a more specific driver for your particular card. You may also want to check the refresh rate ranges of your monitor.

---

### Post by bodhi.zazen on 2006-10-30
> **hawkmooth said:**
> I don't get it... :confused: 

Why can't i choose from the all the resolutions in xorg.conf?

Try this thread, it should at least get you started in the right direction....

[How to Monitor Resolution](http://ubuntuforums.org/showthread.php?t=269052)

---

### Post by ahaslam on 2006-10-31
As far as I know, the 'vesa' driver only supports up to 1024x768. To obtain your desired resolution you'll need to install a more specific driver. For example mine is set as 'via' as I have Via Unichrome graphics. Using the correct driver will also significantly increase the performance of your computer, as your cpu is currently doing the gpu's job.

If you're still having problems, let us know what graphics card you have, someone here will have the same and be able to help ;)

Tony.

---

### Post by shushu on 2006-10-31
Hi, 

I read the topic because I have the same issue.
I have an ATI video card and an IBM p260 monitor, I have tried to edit the xorg.conf file with no success :(

From do I install driver?

Thanks,
Oded

---

### Post by CatKiller on 2006-10-31
> **shushu said:**
> From do I install driver?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by elvum on 2006-11-07
hawkmooth: enable the universe repository and install "915resolution".  That works perfectly on a fresh install of Edgy.

---

### Post by igknighted on 2006-11-07
> **CatKiller said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Yuck, ATI proprietary drivers... I would strongly recommend using the 'ati' or 'radeon' open source drivers rather than ATI's proprietary 'fglrx' drivers.  I would recommend viewing this page [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) for instructions on how to get the radeon driver working.  This will have the added benefit of letting you use aiglx instead of xgl if you choose to install beryl down the road.

EDIT: The above works for ATI cards x8XX and prior, anything x1XXX and beyond you are stuck with the ATI binaries for now

---

### Post by hawkmooth on 2006-11-07
Thanks elvum. 915resolution worked! I'm so happy... :D

---

