---
title: "Create new partition before existing ubuntu installation"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Melkekartong on 2008-03-11
Hi!
Today, my harddisk is organized like this:

hda1 - NTFS: WinXP
hda2 - NTFS: WinVista
hda5 - EXT3: Ubuntu
hda7 - Swap
hda8 - NTFS: Documents.

I want to remove the Vista partition, hda2 and merge it with Ubuntu's ext3.
The consequence of this will be that neither grub or linux will find the ubunturoot.

What preparations should I make before I remove the (useless:P) Vistapartition?

---

### Post by handydan918 on 2008-03-11
Three things come to mind.

1) Back up your data.

2)Back up your data.

3)Back up your data.

---

### Post by glennric on 2008-03-11
Deleting the partition will cause no problems.  Then try to grow the ext3 (Ubuntu) partition into that space with gparted.  You should make sure your data on the Ubuntu partition is backed up as it may get messed up at this point.  Then reinstall grub.  
You will have to boot to a live CD to do all of this, as you can't change a mounted partition.

---

### Post by Omnios on 2008-03-11
How big are your partitions. Doing the above can be a pain. I am not shure but think gparted will not like trying to resize the partition in front of the existing Ubuntu partition. Another optiion is to deleate the vista partition and format it as ext3. Then move the existing ubuntu files to the new partition. Problem with this is grub as it will look for the boot info on the exsisting Ubuntu partition. There is a grub section in the wiki where you can run grub and correct all this. So if you can correct grub then you would be able to expand the new ubuntu part to the right of this partition.
 
Another possiblity is you only need about 30 or so gig for the root partition. Taking this in account you could reformat the vista partition as ext3 and use it to mount your /home files so all your personal files can be stored there.
 
Aso with xp you can still format your documents drives as ext 3 and use the ext program for windows to mount it and even set it up to act as a documents drive for xp. So say you have /home in ubuntu you can make a file in there or use the /home as your doc drive.
 
 Also I just used the gparted boot disk to remake my doc server and it works really well for this as your ubuntu parts are not mounted and you can not tweek a mounted part in ubuntu.

---

