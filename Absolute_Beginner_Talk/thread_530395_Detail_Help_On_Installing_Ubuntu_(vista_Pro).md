---
title: "Detail Help On Installing Ubuntu (vista Pro)"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by L.A. on 2007-08-20
first of all i would like to salute all forum members as this is my first post. i only have a few basic questions i couldn't find any answers to searching through here and google for a bit. if i missed it i apologize in advance and if you would be kind enough to redirect me to the appropriate link it would be appreciated.

I have chosen to download the kubuntu live cd but i have not partitioned any hd's due to these questions.. 

questions
#1.) option A: i have an external hard drive with over 200gb of free space *IF* i can use this HD for Ubuntu how would i go about doing that? when i enter the live cd will it just let me choose which drive to use for space or do i have to partition external hd's aswell?

#2.) option B: i also have a c drive with over 60 gb of free space out of 100+ gb total.. if i want to use ubuntu as my primary OS and want to use it for downloading and using music software... how much space should i partition for this? 

#3.) when everything is set up and ready to go will it read my wireless connection easily?

#4.)  will i be able to choose between using kubuntu and vista at boot up?

note: i have never partitioned a drive before

thanks in advance :]

---

### Post by eapache on 2007-08-20
Welcome to Ubuntu.

When you run the install, it should detect both hard-drives (internal and external), and give you various options. If the 'use largest contiguous free space' option is available for your external, use that, otherwise use 'resize and use freed space'. I suggest you defragment your hard-drive first through Windows to make things even easier for the installer.

Your wireless connection depends on what wireless card you use. Please post the brand and model.

You will be able to choose which OS to load at boot-up, however, the list of possibilities is stored in Ubuntu. If you install to the internal you shouldn't have a problem, however, if you install to the external, the external drive will be needed to boot into vista (if you boot without the external drive plugged in, then it will give you an error.)

---

### Post by L.A. on 2007-08-22
is there anything i can do about vista not loading up with out the external?

---

### Post by eapache on 2007-08-23
Yes, there is, but this will get complicated. When it asks how you want to partition your hard-drive, choose custom. When the partitioner loads, make sure you see two drives, and make sure you can identify which is your internal and which is your external.

On your internal drive, you should have one ntfs partition taking up the whole disk (this is vista). Use the resize command to shrink this just a bit at the end, so you have maybe 200 MB of free space after it. Now right-click and use 'create new partition'. Make it fill the entire space you freed, and make it primary ext3. Under the 'mount point', use```
/boot
```it may be in the dropdown list.

Now on your external drive. it should also be one large ntfs partition which contains the data on it. Use the resize command to open up as much free space as you want ubuntu to have, then 'create new partition'. Make this partition at the beginning of the free space, and make it as large as 2x the amount of ram in your machine. Make it linux-swap. Now create a primary ext3 partition in the remaining amount of free space, and set the mount point to```
/
```

That should do it. If your disks aren't laid out like that, please change nothing and post a screenshot  of the partitioner.

---

