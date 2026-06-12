---
title: "graphics problems continued"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by keno.mentor on 2007-11-20
In my attemps to get my S3 unichrome pro IGP video chipset working in kubuntu I have tried using dkpg-reconfigure xserver-xorg in order to select the higher resolution (my original problem was that I could not select higher than 800x600 in system settings). Before I get to the part about screen resolution, I go through a bunch of other steps which presumably cause some fatal change because this course of action always ends up in kubuntu booting to a text screen (I have reinstalled 3 times now). So my questions are:

1) Is there some way to edit the xconf or xorg file so that I can edit only the part about screen resolution so I don't end up messing up other settings? I've tried a kate command a while back but that required me to be logged on as "root". (?)

2) What is "xserver", "xorg" & "xconf" and how do they relate? One of my problems with all this is that I am a complete newbie and don't understand what these commands mean on a fundamental level.

One other point: The splash screen (the one with the progress bar) is in perfect resolution, as is the logging off splash screen. The login screen is pixelated and in poor resolution

Many thanks,
keno

---

### Post by master_kernel on 2007-11-20
1. You can edit your xorg.conf with the following command:
```
kdesu kate /etc/X11/xorg.conf
```

2. The X Server is the most common graphical window server Linux uses. It can be configured to use window managers such as KDE, Gnome, IceWM, Fluxbox, etc.

Xorg is the X Window System that the X Server uses. It controls your screen resolution and has the settings for you video card and/or monitor.

Xconf is something I have never heard before.

The splash screen is in correct resolution because you have the correct VGA setting in your GRUB file; The X Server does not control it.



This probably doesn't make much sense to you, but hopefully someone can explain it better.

master_kernel

---

### Post by kyphi on 2007-11-20
Assuming that you are using a 'normal' display screen rather than a wide screen, if you use the following code you will go to resolution selection only:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Use your up/down arrow keys to scroll to the desired resolution then press the spacebar to select.  Save and exit.

Reboot.

---

### Post by keno.mentor on 2007-11-20
Master kernel:

I tried running kdesu kate... but it gives me a window with xorg.conf listed in the left panel and no other text anywhere i.e. there's nothing to edit

Kyphi:
When I run dpkg-reconfigure -phigh... it only lets me select the driver (vesa in this case) but does not go on to the screen where the resolution is specified.  It just closes, the screen flashes a bit and then comes back to the terminal

Thanks,
keno

---

