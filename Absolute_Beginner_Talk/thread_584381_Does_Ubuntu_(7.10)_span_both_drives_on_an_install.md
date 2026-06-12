---
title: "Does Ubuntu (7.10) span both drives on an install?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by electronbee on 2007-10-20
I have two 250GB drives and I had Gutsy do its thing for what i thought was the primary. I did not have anything on the second drive but I was just curious if Gutsy decided to span them both.

And, just for my own info, can I to un-span them if I ever wanted to?

thanks!

eb

---

### Post by dpar on 2007-10-20
Gutsy will NEED less than a tenth of one drive. It will use all of it(if you want it to), or you can partition it however you like. I don't think it will do anything to the other drive, other than recognize that its there.

---

### Post by electronbee on 2007-10-20
Hrmm... In disk usage analyzer it says I have 452.8GB total. This is good.

My second HDD device is /dev/sdb1 and the mount point is /media/disk

So, under "Places > Disk" should be my second drive? Also, I can't seem to make a new folder there. I'd like to move my podcasts there...

Thanks again...

eb

---

### Post by dpar on 2007-10-20
What file system is the second disk formated as?

---

### Post by electronbee on 2007-10-21
Disk usage Analyzer states the filesystem type as ext3.

Originally, the two were part of an XP setup. 

I take it I have to use a command line to format the second guy?

---

### Post by electronbee on 2007-10-21
I added Gparted... its there and I can cd via terminal and with:

sudo mkdir test

I can make the test directory and cd into it... 

So, its a permissions issue... so, uhh, how do I fix that for my login?

---

### Post by electronbee on 2007-10-21
Any ways, I need to alter my fstab to add something like this I think:

/dev/sdb1 /media/disk ext3 defaults,users 0 0

This correct?

---

