---
title: "Where/how to mount main linux partition?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by noodles12 on 2006-07-30
So i am in the knoppix live cd and it automounts my sda4 partition to /media/sda4. I have enabled write access for that drive ( knoppix live cd rocks!)

My question is how and where should i mount my sda4 (linux) partition so that when i restart my computer and boot from grub it will load up normally. I know i need to set a mount point, mount the drive, and then edit the fstab but i really don't know in which directory to mount this partition. I think it should be in root but i'm new to linux and really have no idea. 

Thank you for your help.

---

### Post by Drakkor on 2006-07-30
Will this be a Ubuntu machine,or dual boot ?

---

### Post by taurus on 2006-07-30
You can mount it anywhere you want but if you want it to appear on your desktop, then you need to mount it under /media...  And yes, you can specify where to mount with whatever options you want in /etc/fstab!  If you can do it under Knoppix, you can do it under Ubuntu as well.

---

### Post by noodles12 on 2006-07-30
Sorry I forgot to mention that this is an ubuntu installation. This was my main ubuntu installation that never fully worked because it hung at the "mount root filesystme" right at the beginning. I then realized that my sda4 which fdisk -l showed that it was recognized as my linux partition was not recognized by the bash shell or the kernel when it started up ubunu. 

I used the knoppix live cd because it is awesome and was told it would automount my partitions to make it easier for me to read/write and is the top live/recovery cd on distrowatch. 

Where do i mount /dev/sda4 so that when i go into grub and select the top ubuntu installation ( my mian one) it will work. I mounted it on the "/" and i still get that "/dev/sda4/ does not exist. Is it possible that it is mounted but the permissions denies my ubuntu from reading and loading up linux?

If yes, how do i change permissions?

Thank you for your help.

---

