---
title: "how to change file permission"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by edwin11k on 2007-08-07
HI !

I have two external hard disk drive, and try to transfer file from one to the other.  The problem is that when I was trying to copy the file to the new hard disk drive , it does not let me because the hard disk drive is write protected by default.  
 Would you tell me how to change the permission of the new directory???  I could login as root also, but it did not let me change file permission either.  

thank you

---

### Post by Inxsible on 2007-08-07
what is the file system on the drive being copied to ?

if it is ntfs, have you installed ntfs-3g to gain write access ?

---

### Post by AlexenderReez on 2007-08-07
i guess your external harddisk is ntfs partition right?...hm....you need to install ntfs-config ....check this out:)


> [http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by tprzepiorka on 2007-08-07
Hi,
You will need to install "ntfs-3g". If you go to Add/Remove Applications search for "NTFS" and install the one result. Then go to Applications>System Tools and opent the NTFS Configuration utility and tick both boxes.

That should work, assuming the drives are formatted as NTFS.:)

---

### Post by edwin11k on 2007-08-07
HI! Thank you for replies...  I am very beginner in linux, honestly didn't understand ntfs..  

Here is what happened:  I was trying to install ubuntu in my computer, but realized didn't have enough space. So, I somehow tried to install it on the external harddisk drive(which I have been using for window), and ended up partitioning it with some program  in ubuntu. 
 Later, I realized that I could access to only very small part of the external hard disk space, so I moved all the file to the other external harddisk (which was originally formatted for redhat linux) with hope that reformatting(in window) will remove the partition(but no avail)..  Now, I was trying to move back the data from the other hard disk drive to the one original, but whenever I tried , the original harddisk drive claimes to be write protected.

---

