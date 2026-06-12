---
title: "Cannot start X window"
date: 2008-01-14
forum: Apple PPC Users
---

### Post by In_the_wired on 2008-01-14
Helo everyone!

I've upgraded my Ubuntu 6.06 PPC to 7.10, using the alternate cd text installation, in a PowerBook G4. There aren't error messages during the installation, but when i try to start the new installation X Window can't start. The output is this:

```
X Windows System Version 1.3.0
Release Date:19 April 2007
X protocol Version 11, Revision 0, Release 1.3
Build OS: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current OS: Linux ubuntu 2.6.22-14-powerpc #1 Sun Oct 14 21:43:06 GMT 2007 ppc
(...)
(WW) ****INVALID IO ALLOCATION**** b: 0xf0000400 e: 0xf00004ff correcting
(EE) end of block range 0xefffffff < begin 0f0000000
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons (...)
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining
```

I've tried changing xorg.conf, to use differents drivers (fbdev, vga, ati) but remain the same error (only are different the last two "(EE)" lines when use a different driver)

The graphic card is ATI RAGE 128 Mobility 2x AGP

in xconf.org says
```
Section "Device"
Identifier "Ati Technologies Inc Rage Mobility M3 AGP 2x"
Driver "ati"
BusID "PCI:0:16:0"


```

Thank you for helping me!!! :)
Byee!

---

### Post by Gen2ly on 2008-01-15
This looks like a driver issue.  From this error I would deduce that the xorg server cannot find the vesa driver.  I can't remember the configure xorg-server command in Ubuntu but there is a configurator.  Its something like dpkg xorg-server --configure and that I believe installs the driver.

---

### Post by curly_nostrill on 2008-01-15
I don't really know much about Gutsy but I've seen many posts where people have similar problems after upgrading to Gutsy.  I figure you have an older iBook maybe?  I have a g3 dual USB iBook and Feisty works fine.  I'm not going to even try Gutsy.

Elsewise you should search the forums for the fixes... It's in here somewhere.

---

### Post by stream303 on 2008-01-19
> **Dirk.R.Gently said:**
> This looks like a driver issue.  From this error I would deduce that the xorg server cannot find the vesa driver.  I can't remember the configure xorg-server command in Ubuntu but there is a configurator.  Its something like dpkg xorg-server --configure and that I believe installs the driver.

Have you tried
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

note: NO space between dpkg-reconfigure

---

### Post by In_the_wired on 2008-01-20
Yes, i have tried dpkg-reconfigure xserver-xorg with and wihout -phigh (wihout -phigh you can reconfigure more parameters manually)... but appears the same error :(

---

