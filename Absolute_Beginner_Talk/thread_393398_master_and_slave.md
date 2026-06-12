---
title: "master and slave"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-03-25
OK, I am a little iffy about my master slave configuration on my Hard drive, so I was wondering, If I screw it up, will It be unfixable, or can I change it after.
thanks



-sam

---

### Post by sewercake on 2007-03-25
HI
I just installed a new hard drive, but I am unsure about the master slave configuration, I haven't actually turned it on yet, because I am afraid it might wreck my system if I did this wrong, so will it? Or could I go back and change it without killing my system.
thanks a bunch



_Sewercake

---

### Post by jerryrw on 2007-03-25
If you don't get the master and slave settings right your comp will not boot.  It will MOST LIKELY not damage anything but it is possible.  Assuming(correct me if I'm wrong)  that you have a fairly standard setup you most likely had One hard disk connected to the Primary IDE controller and a cd/dvd rom connected to the Secondary IDE connector.  Your original Hard Disk was in one of two states MASTER/SINGLE or Cable Select(CS).  To add a second disk to this controller you need to change this jumper to MASTER with SLAVE check your drive specs for the right one.

Keeping this drive as the master will keep it first in the boot priority and save headaches later especially if you already have GRUB installed on it.

The next thing to do is to set the new Hard disk to slave.  Again check you disk specs for the right jumper settings.  


Another option is to place the drive on the secondary controller, the cable with the CDROM.  If the speed of this controller matches the drive you can get some speed improvements py keeping disks on separate controllers.  the basic procedure is the same just change the Jumper on the CD drive to either master or slave and set the jumper on the New HD to the other.

Remember that after you get the new HD up and running you have to partition and then format it with a new file system.  If you plan to use this disk with Linux then don't use windows to do the partitioning or formating.

Good Luck

---

