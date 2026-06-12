---
title: "Video card settings don't transfer from Live CD to Install"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by petrockthief on 2006-07-22
I get a great resolution when I boot from the Live CD, but after installing, it appears that Ubuntu cannot find the drivers or something- the resolution is shrunk to 640/256. What do I need to copy from the live CD onto the install?

---

### Post by skale on 2006-07-22
in the menu, go to Settings > Display settings and see if changing the resolution helps.

---

### Post by petrockthief on 2006-07-22
> **skale said:**
> in the menu, go to Settings > Display settings and see if changing the resolution helps.

I can't change the any setting underdisplay if I don't boot from Live.

---

### Post by robio376 on 2006-07-22
It would help if you would list the hardware you are using to better help you. Mainly what videocard do you have. and what monitor you are using.

---

### Post by petrockthief on 2006-07-22
The monitor is just a flat screen (not lcd) plug and play. The manufacturer is KDS USA. The graphics card is S3 Savage4, detected on either boot sequence, but the resolution can't be changed from a hd boot.

---

### Post by taurus on 2006-07-22
Reconfigure your X again with (from a terminal)...

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by petrockthief on 2006-07-22
I tried reconfiguring the X server but with no luck. When I go to display and click test on the hardware tab it says that the video card driver configuration and monitor don't appear to work. The details button reveals nothing. I know its not a compatibility issue because I get a great resolution when I boot from Live. :-k

---

### Post by taurus on 2006-07-22
I assume you are at a console (prompt) so maybe you need to edit your /etc/X11/xorg.conf and change the Drive from whatever it is right now to vesa...

```

sudo nano /etc/X11/xorg.conf

```

---

### Post by petrockthief on 2006-07-22
Hmm, I tried reconfiguring the X server a second time, choosing "S3 Saveage" as the driver instead of the default selected "Savage". I set the resolution to 1280/60hz, 24 bit color, didn't work so I tred rebooting (maybe I should have done that in the first place?)  now it won't boot up. I'm using Kubuntu if that makes any difference sorry I forgot to mention it.

What happens is it will go through the whole bought process, everything checks out OK then the screen flickers with lines and such for 20 seconds then I just get the Kubuntu logo with a bar that won't progress.

---

### Post by taurus on 2006-07-22
Now that you already have /etc/X11/xorg.conf, hold <Ctrl><Alt>F2.  Log in with your username and password.  Then at the prompt, edit your /etc/X11/xorg.conf and use vesa as Driver instead of whatever it is right now.  Then reboot and see if X starts or not...

```

sudo nano /etc/X11/xorg.conf

```

---

### Post by petrockthief on 2006-07-22
Ctrl+Alt F2 yielded a frozen screen just as before and it appears I don't have and x11 folder, I went into recovery mode and searched for it with no luck

---

### Post by taurus on 2006-07-22
> **petrockthief said:**
> Ctrl+Alt F2 yielded a frozen screen just as before and it appears I don't have and x11 folder, I went into recovery mode and searched for it with no luck

It's a capital X as in X11, not x11!!!  Linux is case sensitive so X is NOT the same as x...

---

### Post by petrockthief on 2006-07-22
Thanks for clearing that up

How can I get into a text editor from the recovery console?

---

### Post by taurus on 2006-07-22
If you are in the recovery mode, you are logged in as root and already at the console.  So, just edit it by typing

```

nano /etc/X11/xorg.conf

```

---

### Post by petrockthief on 2006-07-22
It says no such file or directory when I try to save

---

### Post by taurus on 2006-07-22
> **petrockthief said:**
> It says no such file or directory when I try to save

:confused:  :confused:  :confused: 

You did type capital X for X11 and small x for xorg.conf, right!  What is the output of this command then...

```

ls -la /etc/X11

```

---

### Post by petrockthief on 2006-07-22
total 92

...

-rw-r--r-- 1 root root 4054 date xorg.conf
-rw-r--r-- 1 root root 4128 date xorg.conf.20060722130505
-rw-r--r-- 1 root root 4071 date xorg.conf.20060722131853

...

I hope that's the right information you need.

---

### Post by taurus on 2006-07-22
> **petrockthief said:**
> total 92

...

-rw-r--r-- 1 root root 4054 date xorg.conf
-rw-r--r-- 1 root root 4128 date xorg.conf.20060722130505
-rw-r--r-- 1 root root 4071 date xorg.conf.20060722131853

...

I hope that's the right information you need.

Well, there it is, xorg.conf in /etc/X11!!!  Again, if you boot into recovery mode, you don't even have to log in because you already log in as root!  And if you have to use your login name and password to log in, then you need to put the sudo in front before you can edit any system file...

```

sudo nano /etc/X11/xorg.conf

```

---

### Post by petrockthief on 2006-07-22
Oh man thanks! I figured out I wasn't opening the file correctly or something, don't feel like explaining it. Anyway everything looks great, but I do get an error message on bootup:

The process for the media protocol died unexpectedly

---

### Post by taurus on 2006-07-22
> **petrockthief said:**
> 
The process for the media protocol died unexpectedly

Hmm...  I've never seen that error message before!  What does the line before the error about the media protocol say?

---

### Post by petrockthief on 2006-07-22
Error - KDesktop

---

### Post by taurus on 2006-07-22
So you are using KDE!!!

---

