---
title: "Blank Screen on install iMac G3 DV SE+"
date: 2005-02-11
forum: Apple PPC Users
---

### Post by Lukas on 2005-02-11
Ubuntu is not detecting the monitor settings on my iMac G3 (Newworld).  
The install runs fine until it loads into the X windows environment when the screen goes blank but still continues in the setup as I can hear the start up sound and the harddrive continuing to tick over. 
Is this a known bug and is there any workaround for it?

---

### Post by chascon on 2005-03-09
You have to reconfigure XF86Config.  You horizontal and vertical have to be set right.  Boot in to OS 9 or OS X to get specs (res [vertical and horizontal] and monitor freq).  You montor freq has to also be set correctly.
Play with it, google some sample Configs for your model.

try "dpkg-reconfigure xserver-xfree86" from conole and select with framebuffer or without.  I find only one works, else X doesn't work.

Which iMac is it? DV?  DV SE? Beige G3?  There are lots of G3s.

---

### Post by lugan327 on 2006-11-14
I am experienceing exactly the same problem on a G3 with 128ram.

While installing, booting from the CD for the first time, the screen goes blank after the splash screen.  A few minutes later there is a tone from the speakers, but the screen is blank.

How can X win be reconfigured **_before _**installing?

Are there boot parameters to set them?

Many thanks, A./

---

### Post by lugan327 on 2006-11-14
Have just found the answer at:

[http://ubuntuforums.org/showthread.php?t=296870](http://ubuntuforums.org/showthread.php?t=296870)

---

