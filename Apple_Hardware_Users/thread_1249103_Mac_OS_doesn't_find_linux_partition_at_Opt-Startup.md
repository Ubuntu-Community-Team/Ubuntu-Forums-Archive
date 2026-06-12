---
title: "Mac OS doesn't find linux partition at Opt-Startup"
date: 2009-08-24
forum: Apple Hardware Users
---

### Post by Cap'n Sarge on 2009-08-24
Hi.  I've got a G3 iBook with 2 bootable partitions of OS X 10.2 and a bootable Hardy Heron partition.  I had a 4th HFS+ partition for scratch, but thought I would reformat it into HFS or FAT32 so both Ubuntu and OSX could read/write.  I was running into permissions issues with HFS+.  Using Gparted on a flash drive, and found that a FAT32 logical 
partition within an extended partition worked well for both OS's, but then found that I couldn't convert the 4th HFS+ to an extended partition due to the mac disklabel, and instead reformatted from Gparted from the 4th HFS+ (6GB) to 3 2GB HFS partitions.  
End Apartheid!  Ubuntu recognized all three; restart to OSX, it recognized all three; restart to Ubuntu to begin file transefer testing, and OSX firmware(?) doesn't recognize the Ubuntu partition any more.  :(  Also, my ubuntu install hangs on shut down.  Restart from ubuntu works fine, but I did force shut down quite a lot until I tried restart.  

How might I get the firmware issue resolved?  

:) 
C.S.

p.s.  It's a ppc.

---

