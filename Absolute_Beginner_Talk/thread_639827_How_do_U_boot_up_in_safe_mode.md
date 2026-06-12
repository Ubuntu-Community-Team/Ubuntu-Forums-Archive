---
title: "How do U boot up in safe mode?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by 4iko on 2007-12-13
OK.When I tried to load Ubuntu I got the following error:
 "cannot display this video mode" ..so the solution I found in the forums was to boot up in safe mode and select last working config..So I did start Ubuntu in safe mode and now I'm getting this:
 boot@myname-desktop:~#
what do I type in here?
 Thanks!

---

### Post by mocoloco on 2007-12-13
When do you get that error, before the login screen or after you type in your username and password?  If you can get to the login screen, click options and change the session to "failsafe Gnome".  If you don't get that far you may have to configure your xorg.conf file to use a lower resolution.

---

### Post by 4iko on 2007-12-13
I get this error before I get to the login screen.Can U pls explain how do I configure my xorg.conf file...
sorry but I'm a virgin...to Ubuntu 
 Thanks!

---

### Post by mocoloco on 2007-12-13
Actually you don't have to manually edit the xorg.conf file, you can use a handy tool to reconfigure your X server (it's what all the graphical stuff runs on top of).  Just boot in to recovery mode and type in
```
dpkg-reconfigure xserver-xorg
```

Follow the prompts, if you don't know what something is just press Enter for the default.  You can probably have it set your screen for you, but if it asks you about resolution just make sure you don't have any selected that are higher than what you're graphics card or monitor support (usually 1280x1024 is a good resolution on most modern monitors, maybe 1024x768 if it's a bit older).

---

