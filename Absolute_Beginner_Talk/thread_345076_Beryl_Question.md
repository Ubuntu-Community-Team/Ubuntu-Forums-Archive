---
title: "Beryl Question"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-01-23
After using the guide on this link: [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

It seems like everything was up and running fine, but when I restart my computer I can't click on the top panel, and the hotkey alt+F2 didn't work, so I went into the terminal and typed in "beryl-manager" and it comes out with this error:

huy@Ubuntu-Edgy-Huy:~$ beryl-manager
huy@Ubuntu-Edgy-Huy:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x5d specified for 0x2803e18 (Could not ).

I don't think the Window manager part and after was there originally, but it appeared before I got to post this thread.

But either way, this is probably why things on Beryl are not working for me. But even if they were, how would I select the preset themes under Emerald Theme Manager. It seems as if you can only import and export themes you made. Well any feedback at all would be great, because  I am quite newbie friendly to Linux :-)

---

### Post by moshuptrail on 2007-01-23
I don't know beryl too well, but it looks like you need to figure out how to get GLX started at boot time.

---

### Post by SilverDragon on 2007-01-23
Oh maybe your right.

I went to System > Preferences > Sessions and added "beryl" and "emerald --replace" already, which I think was on that guide (maybe some other one) but getting GLX started well that's going to be a challenge :-D 

Well I'm going to just try to add GLX to Startup Programs and see what happens.

---

### Post by moshuptrail on 2007-01-23
If that doesn't work, try searching this forum for xgl, or glx and starting.
It might be something that needs to be in xorg.gonf

---

### Post by SilverDragon on 2007-01-23
Well would you happen to know where the "xorg.gonf" file is, just in case I have to change it later.

---

### Post by moshuptrail on 2007-01-23
For starters, oops!  It's xorg.conf   (with a c, not g)
fat fingers

it's in /etc/X11
You usually end up editing it when setting up beryl

example: sudo nano /etc/X11/xorg.conf

BUT FIRST copy it and make a backup!
example: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

---

### Post by SilverDragon on 2007-01-24
Well that looks similar to option 2 on the guide to the link I posted originally. I'll try using option 2, but should I uninstall Beryl and Emerald theme manager first?

---

### Post by SilverDragon on 2007-01-24
uh oh..

Well I just started using option 2 on that guide : [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

and I downloaded a driver (I think it's the right one) and than

sudo nano /etc/default/linux-restricted-modules-common

changed the last line than ctrl+x and y to save

But at the next step with like 6 separate line of code it says:

"Remember that following this method requires a reinstillation of them every time the kernel changes. "

Well I wasn't sure when the kernel changes so I decided to just restart the computer after every line, but now that I think about it, that's probably not what it mean by "reinstillation"? Either way after using this line and restarting

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

it'll load up than show Beryl and than show a black screen with a blinker that allows me to type. So now I can't even get onto Ubuntu :-( and I really have no idea what I should do.

---

### Post by PriceChild on 2007-01-24
You should only have done one of those...

EITHER method 1 OR method 2...

Do this:```
sudo dpkg-reconfigure xserver-xorg -phigh
sudo nvidia-xconfig --add-argb-glx-visuals
```

---

### Post by SilverDragon on 2007-01-24
I would put those two codes into the terminal but I can't get to the terminal, because once I sign in it shows the beryl screen and than changes to the black screen. Should I just reinstall Ubuntu?

---

### Post by jbayone on 2007-01-24
Reboot in recovery mode, then you'll be able to type that in the terminal.

---

### Post by TehMark on 2007-01-24
> **SilverDragon said:**
> Oh maybe your right.

I went to System > Preferences > Sessions and added "beryl" and "emerald --replace" already, which I think was on that guide (maybe some other one) but getting GLX started well that's going to be a challenge :-D 

Well I'm going to just try to add GLX to Startup Programs and see what happens.

you should use beryl-manager instead of just beryl for that part

---

### Post by SilverDragon on 2007-01-24
> **jbayone said:**
> Reboot in recovery mode, then you'll be able to type that in the terminal.

I tried what you said, but I got this error at the bottom:

[17179573.284000] Disabling IRQ #169
[17179573.652000] hdb: WDC WW800BB-00CAA, ATA DISK drive
[17179573.652000] hdd: IRQ probe failed (0xfffffdfc)
[17179573.708000] ide0 at 0x1f0-0x1f7 0x3ff on irq 14

Than it goes on to say hda: lost interupt once every few minutes.

[QUOTE=TehMark]you should use beryl-manager instead of just beryl for that part[/QUOTE]

I will try that once I can get onto my desktop environment :-)

---

### Post by PriceChild on 2007-01-26
> **SilverDragon said:**
> I got this error at the bottom:

[17179573.284000] Disabling IRQ #169
[17179573.652000] hdb: WDC WW800BB-00CAA, ATA DISK drive
[17179573.652000] hdd: IRQ probe failed (0xfffffdfc)
[17179573.708000] ide0 at 0x1f0-0x1f7 0x3ff on irq 14

Than it goes on to say hda: lost interupt once every few minutes.This sounds a much bigger problem than beryl...

I'd check your hardware over, find the culprit.

---

