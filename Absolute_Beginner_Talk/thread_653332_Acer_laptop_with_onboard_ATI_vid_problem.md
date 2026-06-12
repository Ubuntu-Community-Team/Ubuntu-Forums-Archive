---
title: "Acer laptop with onboard ATI vid problem"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Nante on 2007-12-29
I installed ubuntu 7.10 and followed the instructions in the sticky listed in multimedia and video thread,  I got desktop effects working with this but when I tried to run google earth it would lock up and I would have to kill it or reboot (google earth was working using the default driver but WoW needs 3D support) I tried using envy next, now when I load google earth it loads to a screen saying it needs updated drivers then crashes the video (reboots the display like I had pressed control-alt-backspace) anyone know what I did wrong, if more info needed let me know, I am just knowledgeable about ubuntu to be dangerous :)

---

### Post by spiderbatdad on 2007-12-29
what is your vid card? as in ```
sudo lshw -C Video
```

---

### Post by Nante on 2007-12-29
output was:


  *-display               
       description: VGA compatible controller
       product: RS485 [Radeon Xpress 1100 IGP]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx

---

### Post by pHreaksYcle on 2007-12-29
Use the new ATI driver. Instructions with/without Envy included. I actually used Envy now that I think about it. If it fails the first time, retry on new install. (Not saying it will, just in case) Worked for me! Good luck.
[http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html]("http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html")

---

### Post by spiderbatdad on 2007-12-29
I'm not seeing a  better driver for what you are trying to do. I don't think xserver-xgl will meet your WoW needs,  I do see xorg-driver-fglrx-dev in synaptic to go with your current driver. You might make sure you have it.

---

### Post by pHreaksYcle on 2007-12-29
With the new driver, **XGL IS NOT REQUIRED**. XGL does not play nice with 3D apps, that is why I suggested the new driver.
"AIGLX allows you to run hardware accelerated rendering over the GLX protocol, eliminating the need to use XGL for hardware acceleration."

---

### Post by pHreaksYcle on 2007-12-29
No problem :P Glad I could help and watch that site for more helpful guides on ATI cards, that's where I always go first. (Because I'm an admin =))

---

### Post by Nante on 2007-12-29
Tried the new driver and its still crashing, will do a fresh install of ubuntu and try again thanks will post when finished to let you know if it worked or not thanks:)

---

### Post by clayt0njknight on 2007-12-30
I'll bet 10 to 1 that if you disable compiz, googleearth won't crash.

I say that simply because my Gateway MX6454 used the ATi Radeon 1150 (or 200m) video system.  I had the same issues with it and with video playback in Totem and VLC.  I disable Compiz and google earth works fine.  I did, however find a bit of a workaround on the video issue.

---

### Post by Nante on 2007-12-30
Ok did a fresh install and used envy to install new ATI driver, did not enable compiz, it sorta works but now the video flickers, the borders and search section of google earth are stable but the planet display flickers and goes blank every few seconds, I loaded the game Nexuiz to test it and it also flickers, not bad but its annoying. any ideas?

---

