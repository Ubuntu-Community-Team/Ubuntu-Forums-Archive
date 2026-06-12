---
title: "Fixing refresh rate"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Villa on 2007-02-16
Hi I would like to change my refresh rate from 60Hz to something higher, but I'm wouldn't like to use the way pointed out in this tutorial, as it is a bit above me. [http://www.ubuntuforums.org/showthread.php?t=83973&highlight=screen+resolution=p](http://www.ubuntuforums.org/showthread.php?t=83973&highlight=screen+resolution=p)

I once changed my resolution by I'm not sure how, but I went into like this settings screen and I could choose using a GUI what correct resolution I wanted. How would I do that again?

Thanks. =)

---

### Post by laidback on 2007-02-16
System>Preferences>Screen Resolution.

Then you can adjust resolution and refresh rates. The choices appear to be restricted to the capabilities of your hardware, but I cannot swear to that.

---

### Post by ukripper on 2007-02-16
or to go bit advanced option, use console to change xorg, perhaps would be overkill in your case:

$ sudo gedit /etc/X11/xorg.conf                

above will modify or add resolutions/refresh rates you want

---

### Post by Villa on 2007-02-16
Hi I went into the xorg file and changed my monitor specs to:

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    31-101
	VertRefresh  60-100
	Option	    "DPMS"
EndSection

Is that right? Problem is, the the max refresh rate I get is only 60hz, instead of what I want (around 75-80hz) Any help please? =(

Thanks.

---

### Post by ed-j on 2007-02-16
> **Villa said:**
> Hi I went into the xorg file and changed my monitor specs to:

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    31-101
	VertRefresh  60-100
	Option	    "DPMS"
EndSection

Is that right? Problem is, the the max refresh rate I get is only 60hz, instead of what I want (around 75-80hz) Any help please? =(

Thanks.

Caution: Reply from Novice!

What sort of monitor do you have? CRT? TFT? What size? What is your Graphics card or adapter? Which Ubuntu?

---

### Post by Luk0r on 2007-02-16
I'm currently getting a problem where the max refresh rate I can select on the 'Screen Resolution' dialog is 58, I've messed with the xorg.conf no end and cannot get it to increase.

I have a BenQ FP71V LCD monitor.

---

### Post by ed-j on 2007-02-17
> **Luk0r said:**
> I'm currently getting a problem where the max refresh rate I can select on the 'Screen Resolution' dialog is 58, I've messed with the xorg.conf no end and cannot get it to increase.

I have a BenQ FP71V LCD monitor.

I think the highest refresh on an LCD is 60Hz, but without any flicker. They are not the same as a CRT int that respect. If you are happy with the resolution, you have no problems.

---

### Post by Villa on 2007-02-17
Hi my monitor is a CRT, and I have a ati 9200se.

---

### Post by ed-j on 2007-02-17
> **Villa said:**
> Hi my monitor is a CRT, and I have a ati 9200se.

Hi! Anything I can help with?

---

### Post by Villa on 2007-02-19
Yep. =) My refresh rate is stuck at 60hz max. I know it can go higher (on an xp comp), I've edited the xorg file to the below, but all it did was introduce 47hz and 45hz as well. =(

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 31-101
VertRefresh 60-100
Option "DPMS"
EndSection

---

### Post by Penguin Power on 2007-02-19
The problem is that the Screen Resolution tool is a bit limited - but editing your xorg file manually can cause more problems than it fixes.

If you run 
**sudo dpkg-reconfigure xserver-xorg**
in the terminal you will get a configuration utility that allows you to set your refresh rates and resolution without manually editing your xorg file.

---

### Post by Villa on 2007-02-19
Sweet thanks Penguin Power! That fixed it all up to 85hz refresh. ^^

Now if only I could change my res back to 1280*1024... (now it's changed to 1024*800, dunno how =/)

---

### Post by fearpi on 2007-02-22
> **ed-j said:**
> I think the highest refresh on an LCD is 60Hz, but without any flicker. They are not the same as a CRT int that respect. If you are happy with the resolution, you have no problems.

I have an LCD screen that I used to run at 75 Hz. It was visibly smoother than at 60 Hz.

---

