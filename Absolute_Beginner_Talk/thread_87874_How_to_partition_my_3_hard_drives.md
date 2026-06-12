---
title: "How to partition my 3 hard drives"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by mitchy_g on 2005-11-09
Hello,
My PC has 3 (small) hard drives and I have breezy running at the moment, only on the Primary drive, I am wondering how what mounting points i should use so the other 2 drives can be used.

Thanks
Mitch:)

---

### Post by LHZ on 2005-11-09
Common wisdom says to mount additional drives either in /media (if you want to keep them seperate) or on /home or /usr if you need the additional space for personal files. I, for instance, have a seperate large HD mounted in /media/storage to hold music and movie files.

Your harddisks will be in /dev, numbered as follows:

/dev/hda - Primary Master
/dev/hdb - Primary Slave
/dev/hdc - Secondary Master
/dev/hdd - Secondary Slave

Different partions add a number: hda1 is the first partition on the primary master, hdb5 is the fifth partition of the primary slave. You always have to mount a partition, even if there's only one on the drive (no mounting 'hdc', use 'hdc1' instead).

---

### Post by rajsarkar on 2005-11-09
It seems you are a newbie. 

So let me explain you in simple terms. You need to mount your other two hard drives to be able to access them. In linux you need to mount all drives in order to access/use them. 

I hope you have already formatted the last two drives during installation, if not then use the Breezy install CD to format them suitably for linux.

You will get detail of how to mount in [www.ubuntuguide.org](www.ubuntuguide.org)

You would also need to modify etc/fstab (so far I can remember) to write down the mounting options permanently. you will again get the detail in the above mentioned website.

post if you find any problem.

good luck :D 

Raj

---

