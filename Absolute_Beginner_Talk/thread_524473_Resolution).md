---
title: "Resolution:)"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Stefff on 2007-08-13
Hi!
I'm using LG 700 s (old CRT monitor, great reliability) and GForce FX 5200 128 mb.
(2.6 GHz, 1 GB of RAM - Intel P4 processor)

I switched to Ubuntu few days ago...

Maximum resolution is OK - 1280x1240 (I'm using 1280x960), but my refresh rate is 63 maximum:(
My eyes will fall out if I don't change somethin'. 
Maximum refresh rate on Windows was 85 hz, and it was great.

Is there a possibility to switch to 85 hz refresh rate on Ubuntu?

Thnx in forward!

S. :guitar:

---

### Post by tdrusk on 2007-08-13
I THINK you need 915 resolution.

---

### Post by bjarneh on 2007-08-13
easiest way is usally just to reconfigure Xorg using dpkg (sudo dpkg-reconfigure xserver-xorg) then set the refresh rate to 85 Hz..... or search for Horisync on this forum and i'll bet you see plenty of answers  :-)

---

### Post by Stefff on 2007-08-13
THNX mate:)

---

### Post by alienexplorers on 2007-08-13
You could try adding a modeline to your monitor section of your xorg.conf file.  To generate a modeline goto:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

