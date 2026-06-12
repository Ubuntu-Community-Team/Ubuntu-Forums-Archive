---
title: "accessing a physical disk in VMWare"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by ac251404 on 2007-02-16
I have VMWare running in Ubuntu with XP-MCE installed to stream to my xbox. Ubuntu and VMWare run from /dev/hda and I have a 400gb sata drive formatted as ext2 on /dev/sda. Now I had been struggling for a while to add the 400gb disk as a physical drive in the vmware machine because my user wasn't in the disk group. I finally fixed this and it appeared to add the disk fine, but it does not show up in 'My Computer' inside the vm. I tried 'Add New Hardware' but that didnt work and I'm not sure where to go from here. Is there some way I can access the disk as if it were another HD in windows?

thanks

---

### Post by veloce on 2007-02-17
I'm getting a bit out of my areas of understanding here, but two thoughts:

[LIST=1]
[*]I didn't think windows could read ext2 disks?  

[*]If you're sure it should be able to, check the virtual bios settings of the vm - does it see the hard disk?
[/LIST]

---

