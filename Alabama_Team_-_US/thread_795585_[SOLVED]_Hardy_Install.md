---
title: "[SOLVED] Hardy Install"
date: 2008-05-15
forum: Alabama Team - US
---

### Post by retiree on 2008-05-15
I'M planning on installing Hardy soon and I want to leave Gutsy in it's place. What is the best way to achieve this? I have read that, I believe it was Crane, who put certain folders he wanted to keep in different places in case I mess up and have to reinstall. Can I resize my Gutsy partition to accomplish this? Thanks,Retiree

---

### Post by crane on 2008-05-15
You should be able to resize via the installer. If not there are a couple of programs available that can resize your partitions for you. If you plan on doing a separate install (to a different partition) then you items in your gutsy partition will be un effected. If your hard drive is big enough try making 2 extra partitions when you resize. You could use an extra 20 gig or so partition for storage. Once you have it set up just copy you home folder over to it. Then when you get Hardy installed you can just grab what you need from your storage partition. IF the install completely fails then you can reinstall gusty and copy everything back.

 The partitioner can seem a bit "scary" during install. one thing to really look into though is your mount points. Once you create your new partitions pay attention to what they are. Example: if you make 1 20 gig partition for storage and another 20 gig for Hardy. Be sure to note what they are.
 say the first 20 gig is hda3 and the second is hda4. Now you have to determine which will be your storage and which is OS.(and remember to write it down)
OK during partitioning you select the partition for the OS, say hda3 and select it's mount point as / (root). then be sure to select format this partition.
 Now select your partition where your have backed up everything, hda4. When you select edit go to mount point and manually enter where you want it mounted. Say /usr/local/Backups. I wouldn't suggest mounting in your home directory just as a safety precaution. Now make sure you have it set to keep existing  data on the partition.
 Once you have everything set and you click next, the installer will show you which partitions it plans to format. if should show just the partition you want to install Hardy on and the swap partition. If something doesn't look right this is your last chance to select BACK and correct it. After the install is complete, you can browse to /usr/local/Backups and copy  anything you need from there.(You will need SU to write to this directory.

 Also, if you dual boot, you can select the partition that has the Gutsy install on it and do the same thing you did with your backups partition. Just mount it somewhere like /usr/local/Gutsy or even just /Gutsy.
Again, be sure to tell it to keep existing data. and when you click next, only the Hardy partition and the swap partition should be listed to be formated. 

 I hope this makes since and helps out.

---

### Post by retiree on 2008-05-16
Thanks Crane
I'm waiting to install when I get a video card I have on order. It's supposed to be here next week sometimes. Retiree

---

### Post by crane on 2008-05-17
> **retiree said:**
> Thanks Crane
I'm waiting to install when I get a video card I have on order. It's supposed to be here next week sometimes. Retiree

Very cool, what kind of card are you getting?

---

### Post by retiree on 2008-05-17
MSI nVidia GeForce 7300 Le Turbo Cache 128MB up to 256MB PCI Express 16.
Retiree

---

### Post by crane on 2008-05-18
Nice card. Let us know how installing it goes.

---

