---
title: "[SOLVED] My Linux Disk will not load"
date: 2008-06-21
forum: Beginner Team
---

### Post by VTT Alps on 2008-06-21
I downloaded 8.04 from windows and copied it to a CD ROM.  Then I set the Motherboard to boot from the CD ROM.   It keeps telling me to insert a system disk.   Any Idea what I'm doing wrong.  Thanks.

---

### Post by pytheas22 on 2008-06-21
Are you sure you burnt the ISO image correctly?  Windows XP doesn't know how to do it properly using the built-in CD-burning software; you need to use a third-party tool.  [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm) is simple and free.

If you're sure that you burnt the image correctly, then I would suggest either burning another copy (make sure the burn speed is low to avoid errors) in case the first one is just corrupt, or try booting your computer to another CD (like your Windows install CD) to make sure that your computer is able to boot to CD properly.

---

### Post by VTT Alps on 2008-06-21
Pytheas22

You are correct,  I didn't burn the disc correctly.   I loaded  InfraRecorder and was able to create a bootable disk.   Now Linux starts to load but fails because of some kind of Input / Output error.   I checked the disk, and it reported there were errors on the CD.   I will try again at a lower burn speed.  

Thank you for your suggestions.

---

### Post by VTT Alps on 2008-06-21
Linux is now running.  Just had to slow the burner down to 8X and got a good boot disk.   Thanks again:

---

