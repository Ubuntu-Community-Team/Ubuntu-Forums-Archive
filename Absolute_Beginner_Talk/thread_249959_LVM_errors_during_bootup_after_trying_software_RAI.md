---
title: "LVM errors during bootup after trying software RAID5"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by ethereal on 2006-09-03
Hi,

  I recently installed kubuntu 6.06 and tried to setup a raid 5 array of 4 250GB drives.  I was following along with the guide here: [http://gridpt1.fe.up.pt/mlopes/blog/index.php/software-raid-in-ubuntu/]("http://gridpt1.fe.up.pt/mlopes/blog/index.php/software-raid-in-ubuntu/") 
.  After I fdisk'd the 4 drives, I rebooted and got errors during bootup, specifically when reaching: starting Enterprise Volume management System... The error is "*** glibc detected *** corrupted double-linked list: 0x0000000000530c20 ***".  I think I may have made the logical partition occupy the same space as the primary partion on the drives.  (the reason for the logical partition was so that I could used the linux auto-raid fs during fdisk.)  Is there anythink I can do to skip LVM loading and bootup so I can correct this error? ](*,) 

Thanks for any help

---

