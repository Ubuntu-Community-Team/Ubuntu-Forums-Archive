---
title: "Gnome and X blow up, Command line only"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-01-27
While following the

Comprehensive Sound Problem Solutions Guide v0.5e

at: [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

I got as far as:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

and

sudo apt-get install linux-sound-base alsa-base alsa-utils

the next instruction was to reboot. Once that was done I no longer have a graphic desktop. I have switched to my back up hard disk and am online hoping for help.

The next instructions in the Guide said:

sudo apt-get install gdm ubuntu-desktop

will this work without a graphic desktop, that is, will WvDial dial out, and will apt-get install (reinstall) gdm ubuntu-desktop?

I'm asking if doing it from the command line will restore the system to where it was prior to ALSA blowing it up?

---

### Post by taurus on 2007-01-27
See if you get any error message when you run this command from a terminal?

```
startx
```

---

### Post by chalex on 2007-01-27
and yes, the command you plan to run next (sudo apt-get install gdm ubuntu-desktop) will work just fine from the console

---

### Post by Mark_in_Hollywood on 2007-01-27
There is NO TERMINAL. There is THE command line. I am on the 'net and at this forum with the live CD.

Taurus:

startx

started x with a grey/black background and the mouse works, that is the cursor moves on the screen, but nothing else, no panels, no desktop, nothing.

---

### Post by MkfIbK7a on 2007-01-27
try clcking the last link in my signature and following the instructions

---

### Post by AndyCooll on 2007-01-27
Seems like your graphics card hasn't been found correctly. So from your command line:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```
And when you get to the graphics card bit choose "vesa". It's a bog standard graphics card option that works with almost everything and should get you up and running. Once you're up and running you can then start fiddling around finding an optimum graphics card setting.

:cool:

---

### Post by Mark_in_Hollywood on 2007-01-27
Did the following at your X doesn't start?

sudo apt-cdrom add

sudo aptitude update
sudo aptitude install ubuntu-desktop

sudo /etc/init.d/gdm start

the system added the cdrom, updated the repositories and installed the desktop, but it did NOT restart. Same grey background, mouse cursor working, no menus and no panel.

To Andy Cooll

will those commands work without being online? I have to wait to hear from someone about this, as I can't be at the command line and online simultaneously at the moment.

---

### Post by taurus on 2007-01-27
You don't need to be online to reconfigure your X.

---

### Post by thatkidandy on 2007-01-27
i can confirm that this has just happened to me too

you log in, and then the screen is blank with only the mouse?

did you just update the gnome 2 apps or something via update manager?

EDIT: sorry i read to quickly, i am sorry for jumping the gun
unfortunately this is much different situation than mine

---

### Post by Mark_in_Hollywood on 2007-01-27
Did as Andy Cooll said to do:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg

I went through a long re-config Q&A. At the end, the system locked and I had to reboot. My system is little better now than before. Well maybe worse,

Startx still brings up the grey background

sudo /etc/init.d/gdm start

fails and locks the system, keyboard and mouse.

Anybody?

---

