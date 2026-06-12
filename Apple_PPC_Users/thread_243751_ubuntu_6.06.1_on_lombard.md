---
title: "ubuntu 6.06.1 on lombard"
date: 2006-08-25
forum: Apple PPC Users
---

### Post by kenzoida on 2006-08-25
Hi, trying to put Ubuntu on my Lombard using Alternate CD, install went ok and now it boots up with message "[ 23.211249] PCI: Cannot allocate resource region 1 of device 0000:00:11.0" and I'm brought to a text-mode login "Ubuntu 6.06.1 LTS myhost tty1".  Has anyone seen this error?  How can I boot into GUI mode?  Thanks.

---

### Post by fortyfoxes on 2006-08-28
Yes I get the same error message with the standard (not alternate install). First time it booted into Gnome, but now hangs on X.

---

### Post by iamhugeinjapan on 2006-08-28
I've never seen that problem with my Lombard. It's had Hoary, Dapper-Desktop and Xubuntu-Alternate installs.

---

### Post by 3rdalbum on 2006-08-29
Try doing:

```
sudo apt-get update
sudo apt-get install xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

There was a bug in a recent version of xorg that had something to do with PCI devices. The above commands should upgrade to the good version then allow you to reconfigure your video.

---

### Post by fortyfoxes on 2006-09-06
OK - but I am booting from a live CD. So do I boot using "server" and then still I have no base to install the rpms...

From your blog it looks like I can redownload the iso and burn a new CD to fix the xorg issue?

---

### Post by gvigorus on 2007-08-01
I get the same PCI error at boot on Lombard with Feisty Fown
Says PCI:Cannot allocate resource region 1 of device 0000:00:11.0

when i do $ lspci
00:11.0 device is my VGA Compatible Controller: ATI Technologies Inc 3D Rage LT Pro.

Furthermore, my PCMCIA wireless Orinoco card is not recognized. Machine starts slow when PC card is inserted. Power light never comes on.

I have a feeling that somehow PC card is trying to get IRQ that was already given to the video card, no?
Any advice?

---

### Post by radicalspud on 2007-08-02
I was going to create a new post to document my ongoing battle with my G3 Lombard (400 MHz, 384MB RAM), getting 6.10 (Edgy) to install, but since you seem to be having similar problems with an identical machine, i'll try posting here to see if anything i have encountered can help and vice versa.

in sum, i can get Feisty to boot from the live CD all the way to the desktop with no problems, but i can't install because some application crashes in the background and that's that. HOWEVER, it will render everything correctly, but ONLY from the live CD. because of this, i KNOW that it's possible to get Ubuntu to display correctly on my PB.

Edgy live CD, on the other hand, hangs somewhere after the splash screen. the splash looks like OF video only, never has it displayed correctly, and i've never gotten it to boot all the way to the desktop.

via the alternate-install CD, i've had successful installations of Edgy onto my hard drive a couple of times, and it's fine until i try to get Xserver to start, then i ALWAYS get a black screen and i have to restart in single-user mode to do anything else. i have tried EVERY configuration change in xorg.conf to get it to render correctly: 24 bit, 16 bit, 15 bit, "ati" driver, "FBDEV" enabled/disabled, changing refresh rates, adding "VideoRam" option...everything i can find from any post that relates to the G3 Powerbook ATI video chips and...nothing. black screen every time. i don't even know what i'm supposed to see when i run "startx" but presumably it's something more than a black screen. i have not tried Xubuntu yet, but that's the DE i'm going for first if i ever get Xserver to work correctly.

i have encountered the "PCI:Cannot allocate resource region 1 of device 0000:00:11.0" error with some other info about "no screens found" but never on a boot. it's only happened when i've tried to start the xserver manually. my PB also lists "0:11:0" as the PCI address if i use "lspci" but i'm certain that the configuration has to be "0:17:0" because that's what the auto-configuration detects every time. i don't know why there's a discrepancy there (or maybe it's supposed to be that way).

last night i booted from the Feisty live CD and examined the xorg.conf file it uses, then replicated those settings in mine, figuring that if the CD got it to work, i could do the same by using its settings.
still got the black screen though. the CD configuration uses:

Section "Device"
Identifier "ATI Technologies 3D Rage LT Pro"
Driver "ati"
BusID "PCI:0:17:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies 3D Rage LT Pro"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"

etc.... all the modes are listed (4, 8, 15, 16, 24) with only "1024x768" resolution. i tried 'glxinfo | grep "direct rendering"' from a terminal in the live CD and it indicated that DRI was not enabled. i really don't care about this, because the Xserver and DE still work, which is all i'm after.

after the 6.10 install finished last night, i updated the kernel (apt-get dist-upgrade) and then installed xserver-xorg, which should have installed the current version that 3rdalbum was referring to, which fixed whatever bug there was with PCI devices.

i'm stumped. i have spent hours on this and gotten nowhere. the only reason i don't just give up is because the live CD works correctly, at least for DE display, which means it has to be possible to make it work. tonight i'm going to try the alternate-CD install of Feisty and see if that works better.

remaining questions (perhaps someone can shed some light on these topics):

* why would the splash display correctly with Feisty live CD but not with Edgy live CD? and where does the renderer for the splash get its settings?

* does the live CD autodetect xorg settings on the fly or is there some other settings file that it uses that i'm not aware of?

* would an older version of xserver-xorg possibly work better? if so how do install a specific version of it instead of the default (which is 7.1.x) via "apt-get"?

* what should happen when i run "startx" without Gnome, KDE, or XFCE installed (i.e. just xserver)?

sorry for the long post.

---

### Post by gvigorus on 2007-09-07
I am running 7.04 Feisty Fawn on G3 Lombard. I couldn't boot from CD so I did net install and booted from hard drive. Everything works super smooth, all the features are detected and XFCE windowing environment makes this 400Mhz computer feel faster then some Vistas on 2.4Ghz machines that I've tried:) The only issue I have with my install is the PCI:Cannot allocate resource deal. My network ethernet card works great, but I can not get my PCMCIA card to work. I believe that PCI:Cannot allocate resource message at boot is directly involved in PCMCIA Lucent Wavelan Silver not working.
Anyone knows how to get that warning message resolved? Thanks

---

