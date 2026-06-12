---
title: "hard disk problem at start up"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by sudhinma on 2007-09-04
I am a newbee to linux.

I just installed ubuntu 7.0.4. When i installed it i had not connected one of my hard disks which contains lot of data(40 Gb) 

and now after successful installation i connected the scsi hard disk. when ubuntu boots it takes a long time  displaying lot of errors on screen and keeps scanning the hard disk. this goes on for long and the system never completes the disk check. when i disconnect the hard disk it boots very fast without any errors.  

pls let me know how to skip this disk check. or should i reinstall ubuntu with the hard disk connected.


regards

---

### Post by ConradPafford on 2007-09-05
SCSI devices have identifiers and sometimes the placement within the chain determines its ID. I am not extremely experienced with SCSI but it is important to ensure there are no ID conflicts. The ID can sometimes be manually set on the drive itself.

Good day,

Conrad

---

### Post by alienexplorers on 2007-09-05
Just reinstall with the SCSI drive connected and let Ubuntu find and recognize the disk.

---

