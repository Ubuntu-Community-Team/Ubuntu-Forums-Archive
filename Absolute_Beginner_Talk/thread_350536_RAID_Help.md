---
title: "RAID Help"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by mattdwilnew on 2007-01-31
Ok, I have installed 6.10 ubuntu on a separate 80gig hard drive, and i have 4 250gig SATA drives in a RAID with a Promise FastTrak card. When installing Ubuntu i set the 4 drives up into a RAID 5 array with the partitioner, and it seemed to be fine. When i get into ubuntu i cannot access the drives, i can find the sda/b/c/d .

Attached is a screen shot of my device manager. I have honestly searched around for a solution to this, most RAID guide/howtos want me to do it from the install CD, and after the issues i had with installing i do not want to have to do it all over again. I'm sure there is an option i am missing, or I have been going to the wrong place! there is no "c,d,e:' like windows - I am a linux noob.

Thanks for any help you can provide.

---

### Post by mattdwilnew on 2007-01-31
Noone?

Sorry if this seems like a simple question to some, google doesn't really help me much here :(

---

### Post by theh3brewhammer on 2007-02-19
I am having an identical issue except w/ an IDE fasttrack controller.  Are there ubuntu drivers for these?  Thanks.

---

### Post by mattdwilnew on 2007-02-20
I finally got it worked out mate, Check out Software RAID how to's. MDADM is what i used to get it running. 

You need to format each drive into Linux RAID format, then you need to create a RAID with MDADM using the devices, then you need to format the MDADM RAID into a file system ext2/3. Then you need to mount the raid.

Busy at work atm otherwise id help more.

---

