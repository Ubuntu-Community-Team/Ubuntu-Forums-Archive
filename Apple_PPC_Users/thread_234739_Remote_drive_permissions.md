---
title: "Remote drive permissions"
date: 2006-08-11
forum: Apple PPC Users
---

### Post by ubuntubrian on 2006-08-11
I have a 250GB Fantom drive that had been working fine but now I can't copy or write to 2 of the 3 partitions on it. They show up as using hdparm:
root@ubuntu:/ # hdparm /dev/sda13

/dev/sda13:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 105707632, start = 206874160
root@ubuntu:/ # hdparm /dev/sda9

/dev/sda9:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 64789688, start = 1824root@ubuntu:/ # hdparm /dev/sda11

/dev/sda11:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 141558360, start = 65053656

the volume sda9 can be written to but the other 2 give an error of "read-only". This is the case with a pen drive that was working also. I've changed permissions in OS X but that only worked on the sda9 volume and not the others. Any ideas?
Thanks

---

### Post by ubuntubrian on 2006-08-12
OK. I've checked out some other posts now and it appears that this can be a problem with OS X and Linux using the same drive. I formated the drive in OS X to set up partitions too so that must be the problem. Until someone presents a good solution I'll leave well enough alone but would love to be able to write to the other partitions.

---

