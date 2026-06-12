---
title: "Ubuntu Installation on RAID0"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by yfronto on 2006-12-16
Hello, I'm running Ubuntu 6.10 from a live CD right now and I'm trying to install it, but I'm having trouble. I'm running 4 80gig HDs on a RAID0 configuration through the bios with nvidia's raid firmware. XP pro came pre-installed on the machine, and I don't want to wipe that partition just yet, since I use it for work, I want to take free space from the end of the drive and make a new partition from it, then install Ubuntu on that partition. I've done this with just a single harddrive, so I know the process is easy, But the partition loader sees SCSI1 - 4; four different hard drives. I just don't know how to load the Raid drivers. Anyone have some insight on this?

Thanks

---

### Post by yfronto on 2006-12-16
Figured it out. Used dmraid.

---

### Post by yfronto on 2006-12-17
Update: 

Dmraid saw my 4 drives as one, so everything seemed to work fine, I used ntfsresize and then fdisk to make another partition, then I had my 150gig partition for Windows and an empty 175gig for Ubuntu. Everything seemed to work fine, but Grub won't see the drives to boot to, any ideas on how to install dmraid to load before Grub looks at the drives?

Thanks

---

### Post by Rizado on 2006-12-23
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) Maybe this guide will help? I'm about to do this as well (Installing ubuntu on a software raid or whatever it's called). Were there any problems, modules that had to be manually loaded or was recompiling the kernel necessary? 

Another question, will this raid array created with linux be accessible with windows and vv?

---

