---
title: "Monitor Out of Range, user out of ideas"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by unsui on 2007-02-24
Just built a tower from parts (first one!) with some excellent help, got Edgy installed on it, everything set up and working great. Brought it home, plugged a 17" LCD into it, turned it on. Got mobo page, got grub, Ubuntu progress bar loaded all the way up, and then the monitor went black except for an Out of Range message in the middle of the screen. The end.

Switching out a CRT for the LCD gave back a more useful error message. To paraphrase: Out of Frequency: HF 74.9 kHZ, operating range 30 - 71 kHz. Apparently I need to adjust the screen resolution, but I can't do that without access to the boot menu or the desktop, and I can't get either. I can get a command line, but can't figure out how to adjust resolution from there. Booting off a disk didn't work (disk might be Breezy).

Thank you in advance...

---

### Post by houstonbofh on 2007-02-24
First get the scan rates for your monitor.  Then boot to the safe mode.  Run 'sudo dpkg-reconfigure xserver-xorg' and use the monitor settings.

---

### Post by paydaydaddy on 2007-02-24
This copied from another thread:
The usual fix for this is setting your monitor refresh rates in the config file. Be sure to research the correct values for your monitor and enter only the correct info.

Run this command:
gedit /etc/X11/xorg.conf
A text editor should open, showing you the contents of the configuration file. Look through it for a section like this:
Code:

Section "Monitor" 
Identifier "Generic Monitor" 
Option "DPMS" 
HorizSync 28-51 
VertRefresh 43-60 
EndSection

Yours may not have HorzSync and VertRefresh or may have incorrect values. If that's the case, it can stick you at 640x480. You can enter them manually, but make sure you get the correct values or you can damage your monitor.


If you do want to edit that file, run the gedit command again, but put sudo before it. This will allow you to edit it, since you will have higher privileges.

---

### Post by unsui on 2007-02-24
houstonbofh's suggestion just brought back another prompt. paydaydaddy's returned an error: "cannot open display." I changed over to the etc directory and X11 doesn't seem to exist.

Am I even in the right place here?

---

### Post by mgmiller on 2007-02-24
The safest way is to let xorg re detect all the settings.  You should know the horizontal and vertical refresh rates before starting, in case it's not auto detected.  Otherwise, answer the default to most of the questions it will ask.

Even if you have a black screen, you can do ctrl/alt/F1 to get to a terminal, then:

 ```
sudo /etc/init.d/gdm stop
``` (or kdm for KDE)

You can do the whole X configuration process by entering:

```
sudo dpkg-reconfigure xserver-xorg
```

To start Gnome/KDE again:

```
sudo /etc/init.d/gdm start
``` (or kdm for KDE)

---

### Post by unsui on 2007-02-24
Bingo, mgmiller. Actually, I just took a tour once I got into dpkg-reconfigure, and left everything alone except the screen resolution, which I put on the right numbers (it was jacked up to 1900 x something). Rebooted and we're golden. Thanks to all for the assistance! Ubuntu Forums are most excellent!

---

### Post by houstonbofh on 2007-02-25
Doh!  Shows what happens when you type late at night.  I will edit my post to show correct data.

---

