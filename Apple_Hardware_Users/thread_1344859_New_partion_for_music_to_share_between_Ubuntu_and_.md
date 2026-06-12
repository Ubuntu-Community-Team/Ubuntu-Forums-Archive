---
title: "New partion for music to share between Ubuntu and OSX partitions."
date: 2009-12-03
forum: Apple Hardware Users
---

### Post by conal on 2009-12-03
Hello, do any of you have this dilemma?;- 

I have an Ubuntu and and OS X tiger partition on my PPC G4.

I need both for different design applications, but I can't work without music, so I've ended up with the same music on both partitions. 

Would it be possible to;-

1. shrink my ubuntu partition form a live CD
2. reinstall ubuntu on the shrunk partition (also from live CD)
3. format the space I have freed up, as FAT 32 perhaps? to create a new partition (either from ubuntu or OS X) 
4. Move my itunes library to the new partition and access it from both partitions.

Obviously i will have to back up all my documents first, and i can see that messing with the same library from both itunes and rythmbox will cause confusion, but in theory this is possible - right?!

Please let me know if you have tried anything similar!

Best 

Conal

---

### Post by linuxopjemac on 2009-12-03
You can make two partitions from your Ubuntu one after you backed up. Then you make one MSDOS (FAT32) and the other ext3 or ext4. You will probably have to sync the partition tables from rEFIt after this.

---

### Post by conal on 2009-12-03
Thanks linuxopjemac

Glad someone else thinks this would work. 

However I don't think I have rEFIt - is it for powerpc macs or just intel macs?

I have a powerpc mac. I think I need to do more research, I hadn't considered that I would have to do any kind of sync afterwards.

Cheers

Conal

---

### Post by linuxopjemac on 2009-12-04
Sorry, I didn't read well....You have yaboot, you don't have rEFIt (it's for Intel Macs). You won't have to do anything, maybe only adjusting yaboot.conf and then ybin.

See [here ]("http://mac.linux.be/content/booting-newworld-macs-yabootybin")for general information about this.

---

### Post by conal on 2009-12-04
Thanks linuxopjemac, That link will be helpful, I can't ever remember how I got Yaboot setup in the first place!

---

