---
title: "CDROM Freezes System"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by galaxy81 on 2006-07-27
I just upgraded to 6.06 from 5.10 and I cannot use the CDROM anymore.  It worked fine in 5.10.  Everytime I load a disk in the CDROM the system freezes and I have to turn my computer off and reboot.  The computer also freezes if I boot with a disk in the CDROM drive.  I have been looking for a solution for this and all I found was the following:

I have solved it by disabling the dma in the cdrom drive putting it in /etc/hdparm.conf:

/dev/hdd{
dma = off
}

And setting hdparm to start when the machine boots.

Since I am so new to Ubuntu - how do I do this procedure?  I need a step by step solution, not just a "put this in here."   Help please!

---

