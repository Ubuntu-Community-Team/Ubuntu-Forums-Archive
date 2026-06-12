---
title: "Installation - mount points"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by agm_ultimatex on 2006-11-07
I'm just running the installation, and I am not sure what to do for prepare mount points. I have a partition on my master drive which windows is on, I have a second partition on my slave, and about 80 gigs of unpartitioned on my slave, which I want to install to.

Thanks

---

### Post by K.Mandla on 2006-11-07
Try using "guided partitioning", which should grab the largest available unpartitioned space -- that 80Gb you have set aside should work perfectly.

Let us know if it doesn't work. ;)

---

### Post by agm_ultimatex on 2006-11-07
alright, i tried automatic aka guided, it came up saying 
partition #2 of /dev/hdb as ext3 
partition #5 of /dev/hdb as swap

Not sure why it would look at two.

Thanks again

---

### Post by taurus on 2006-11-07
You need one to install Ubuntu on /dev/hdb2, and another for swap, /dev/hdb5.  Those are standard so you are good to go...

---

### Post by K.Mandla on 2006-11-07
It's headed for your hdb drive. Is that the one you want? Your master drive should be hda, and a slave drive should show up as hdb (I'm assuming you don't have other drives attached and your cdrom is on the secondary IDE line).

If that sounds right (check the drive sizes to be sure), go ahead. It makes two partitions -- one for the system area and one for a swap -- think pagefile -- area.

---

### Post by taurus on 2006-11-07
From his original post, his Windows is on the master which is /dev/hda1 then.  And since he has about 80GB free on the slave which I assume you already have a partition on that slave drive, /dev/hdb1, that's why Ubuntu wants to divide that free space into /dev/hdb2 & /dev/hdb5.

---

### Post by agm_ultimatex on 2006-11-07
ah that makes sense, thanks guys. I'm in my first year of computer programming, so I am learning this stuff slowly.

---

