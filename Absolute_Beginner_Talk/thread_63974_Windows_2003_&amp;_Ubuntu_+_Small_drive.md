---
title: "Windows 2003 &amp; Ubuntu + Small drive"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by cb2k on 2005-09-09
Ok so I want to setup a Ftp/ LAN file server. But i dont know which OS to use. I have an old 8 gig hd that I got out of my Xbox. Do you think it would be ok to split the drive into two partisions.. approx 4 each? Is 4 gigs enough for both to run? Or should I give one more room then the other. I dont plan on putting any other software on the machine. Just the OS's and a second HD that will hold on my files.

The reason I want to dual boot is because im a Windows person but I want to learn Linux. So I will be able to get the Windows Server running faster, but still be able to play around with aLunix server.

Also what format should the second HD be so it will work in both OS's?

---

### Post by r_a_trip on 2005-09-09
[QUOTE=cb2k]Ok so I want to setup a Ftp/ LAN file server. But i dont know which OS to use. I have an old 8 gig hd that I got out of my Xbox. Do you think it would be ok to split the drive into two partisions.. approx 4 each? Is 4 gigs enough for both to run? Or should I give one more room then the other. I dont plan on putting any other software on the machine. Just the OS's and a second HD that will hold on my files.

The reason I want to dual boot is because im a Windows person but I want to learn Linux. So I will be able to get the Windows Server running faster, but still be able to play around with aLunix server.

Also what format should the second HD be so it will work in both OS's?[/QUOTE]
 Ubuntu should be very happy with aproximately 3 to 4 Gigs. Don't know about Win 2K3. I left the MS world 5 years ago.

For the second harddrive your best bet is to go with FAT32. NTFS support is not 100% in Linux yet. Don't forget to check out umask=xxx to go in your fstab in Ubuntu. Otherwise only root can access the FAT32 disk. 

I solved it with umask=0. It was the lazy option to enable my BF to access his FAT32 partition. I'll probably get shot by the more security conscious Ubuntu users  ;-) , because umask=0 gives anyone read/write access to the partition.

---

