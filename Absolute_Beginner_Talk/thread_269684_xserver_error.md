---
title: "xserver error"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by hurrikane on 2006-10-02
I'm fairly experienced with computers, but a total noob on the linux side of things.  I'm getting this error after installing...

This seems to be a config problem.  Is there a way I can just use the standard, default config from the live cd?  This works awesome with the live cd, just when installed on the HDD do I get this error.

waiting for X server to shut down FreeFontPath: FPE "usr/X11R6/lib/X11/fonts/misc" 

I haven't been able to find anything on the net which was working.  I've reinstalled xserver, loaded the nvidia driver in accordance with [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper).  No luck.  

Config is a Dell E1505 w/Nvidia 256MB card.  

Thank you in advance!

---

### Post by Kobalt on 2006-10-02
Hi, 

When you say you've reinstalled the xserver, how did you do it ? I mean, which command did you run ? By the way : is it Ubuntu 6.06 you're trying to install ? 
You shouldn't need to reinstall it, just reconfigure it, with the default settings that seem to work with your computer since the LiveCD booted correctly. 
You can try this command line to reconfigure X : 
```
sudo dpkg-reconfigure xserver-xorg
```

Then  restart your computer and tell us what's going on.

Cheerio !

---

### Post by hurrikane on 2006-10-03
I gave the reconfig a shot.  It kinda fixed the problem.  It ran me through the whole reconfiguration application and I'm not getting the same error any longer.  Now I can make a variety of selections and it seems to load, I just can't see anything.  It acts as thought either the resolution or the refresh rate is out of range even though I've selected options which I know the monitor is capable of.  I do successfully see the Nvidia logo and a flash with the "X" mouse and background for just a second, then acts as previously described :c(

One thing I noted is that there is a 'nv' and a 'Nvidia' driver option.  Does anyone know which I should be using the the Dell E1505 laptop with the nVidia GeForce Go 7300?  Or which of the other options may work?  I'll keep messing with it and let you know if I find a working combo.  Thanks for the info!



> **hurrikane said:**
> I'm fairly experienced with computers, but a total noob on the linux side of things.  I'm getting this error after installing...

This seems to be a config problem.  Is there a way I can just use the standard, default config from the live cd?  This works awesome with the live cd, just when installed on the HDD do I get this error.

waiting for X server to shut down FreeFontPath: FPE "usr/X11R6/lib/X11/fonts/misc" 

I haven't been able to find anything on the net which was working.  I've reinstalled xserver, loaded the nvidia driver in accordance with [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper).  No luck.  

Config is a Dell E1505 w/Nvidia 256MB card.  

Thank you in advance!

---

### Post by CatKiller on 2006-10-03
> **hurrikane said:**
> One thing I noted is that there is a 'nv' and a 'Nvidia' driver option.  Does anyone know which I should be using the the Dell E1505 laptop with the nVidia GeForce Go 7300?

The nvidia driver is the non-free driver from Nvidia. You should only select this if you've actually installed the nvidia-glx driver, or the nvidia-glx-legacy driver. The nv driver is the Free driver, from the X.org people I believe.  Which driver you choose depends on your own moral choice.

---

