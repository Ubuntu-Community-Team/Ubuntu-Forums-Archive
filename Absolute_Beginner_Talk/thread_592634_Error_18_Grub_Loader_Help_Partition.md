---
title: "Error 18 Grub Loader Help Partition"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by mr_manson on 2007-10-26
Hi to everybody

I have a notebook ACER Travelmate 803 LMi year 2004 with last bios version (the last official in acer site)

I replaced my old HDD ( broken) with a new one 160 GB but....

When I tried to install XP  for first time it see at max of 130 GB the same for Vista  

 I know  it's a Bios problem but there is no official version and no third part i found)

Then...before install it i see that UBUNTU see the total space of 160 GB so...i thinked...

XP 35 GB Vista 35 GB BACKUP SPACE 60 GB (130 gb) and the rest for UBUNTU 30 GB

So I installed in this Order XP VISTA and UBUNTU....for installation it was all ok but...

when i restart i see GRUB LOADER ERROR 18 ...i see on inet and i understand that is a impossibility to see the grub loader

Cause it was on last partition that is after the 130 Gb...then

So what can I do to made visible the grub loader correctly and use the totally space of HDD

Can in some way move the grub location ?

If i make a ubuntu partition before  130 gb ... for example XP - VISTA - BACKUP 125 GB...so i have 5 GB could be a solution ?

Thanks a lot

---

### Post by sneezymelon on 2007-10-27
couldn't understand you...

---

### Post by mr_manson on 2007-10-27
mmmm
i try to explain

I have a laptop that see XP an Vista at max 130 Gb of an HDD 160 GB this is  a bios problem

With Ubuntu i can see all the hdd....

I installed in order xp vista and in the last partition ubuntu

The last partition start at 130 Gb ...so the grub can't be reached by bios cause is installed in ubuntu partition then after 130 Gb... I think i must take the grub and move to the first boot partition or make an boot partition before all 

I just wonder if there is a solution before try to reinstall all...

Thanks

---

### Post by louieb on 2007-10-27
The normal way to fix this is create a 75 -100 MB partition inside the area that the PC can boot to.  Then when you install Ubuntu you will use the manual partitioning option and when you define your mount points you will mount /boot on that partition. Just remember that you will also have to create and mount partitions for / (root) and swap.

---

### Post by mr_manson on 2007-10-29
Hi...

I try to this this option..but without boot partition so i will retry to install 

Could u tell me what is the best way to do ?

What is the prefer order to install  XP VISTA then UBUNTU ?

and...what is for  every partition XP VISTA UBUNTU (boot root and swap ) is the correct mode ? Primary and logical 

Thanks

---

### Post by meindian523 on 2007-10-29
> **mr_manson said:**
> Hi...

I try to this this option..but without boot partition so i will retry to install 

Could u tell me what is the best way to do ?

What is the prefer order to install  XP VISTA then UBUNTU ?
The preferred order is Windows,then Linux.....

> **mr_manson said:**
> and...what is for  every partition XP VISTA UBUNTU (boot root and swap ) is the correct mode ? Primary and logical 

Thanks

Ubuntu requires 
boot(approx 150 MB is enough),
root(a min of 5GB) and
swap(2*(size of RAM) is recommended).....

Windows doesn't.....
Windows requires to be installed on a primary partition to boot....
Ubuntu does not mind whatever type of partition it's installed to whether primary or logical......

If I got you right,your problem is that the Grub files(kernel and init files) are not within the HDD space which can be accessed by your BIOS therefore Grub is showing error 18,correct?

---

### Post by meindian523 on 2007-10-29
> **louieb said:**
> The normal way to fix this is create a 75 -100 MB partition inside the area that the PC can boot to.  Then when you install Ubuntu you will use the manual partitioning option and when you define your mount points you will mount /boot on that partition. Just remember that you will also have to create and mount partitions for / (root) and swap.

His problem is that he's already installed and wants to rescue without reinstalling as far as possible.....I guess it's possible if he can get some space by resizing his Windows partition..........

---

### Post by louieb on 2007-10-29
I believe the MS products have to be installed on a primary partition. Linux doesn't care primary or logical will work. I gave a suggested size for /boot and /. The others you'll just have to do some research and guess what they need according to how you are going to use your PC. Don't know if you should install Vista or XP first, but its easier to set up multi booting of you install Ubuntu last. 

IF I were going to start over and partition your laptop this is what i'd do:[LIST=1]
[*]primary partiton for /boot 100MB
[*]primary partiton for Vista or XP
[*]primary partiton for Vista or XP
[*]extended partition[/LIST][INDENT][LIST]
[*]logical partition for Linux / (Root) 10 GB
[*]logical partition for Linux /home
[*]logical partition for Linux swap
[*]logical partition for data[/LIST][/INDENT]

---

### Post by mr_manson on 2007-10-29
> **meindian523 said:**
> His problem is that he's already installed and wants to rescue without reinstalling as far as possible.....I guess it's possible if he can get some space by resizing his Windows partition..........

Yes Error 18 

There is no problem to reinstall all 

The last installation was Xp 35 gb - Vista 35 gb - a logical partition all in NTFS 55 total 125 Gb so the bios should be see another 5 gb (130 gb max supported) but i'll never make the boot partition but only a root and a swap and infact there was an error 18 at reboot now i'll try to reinstall and make a boot partition too

But i'm not sure about this

If i want create a logical partition of 55 GB for NTFS when i must to create ?
I think is not possible to do with ubuntu....if i install in ordere XP VISTA when is best way to do it ?

Thanks

---

### Post by meindian523 on 2007-10-29
Try:
1)In your present Vista System,delete the XP partition and make a / partition for Ubuntu,don't format it for now and make a swap partition(2*size of RAM),again don't format it.

2)Now reboot and pop in your XP CD and start building partitions for it from whatever cylinder the above partitioning scheme stopped at...install XP

3)Reboot,install Vista,reboot,install Ubuntu(use the partitions created in <1>).....Now you have the foll disk diagram I hope:
>Extended partition 1:

         >>Logical partition 1[file system:ext3]
              Format during installation of Ubuntu,write Grub to MBR)/ for Ubuntu 5 Gigs(or whatever you choose,just make sure you have enough space to allow XP and Vista System files within your BIOS restriction)

          >>Logical partition 2[file system:linux swap]
              swap (2*size of RAM)

>Primary partition1:file system:(FAT32 or NTFS)

           >>XP C:\

>Primary partition2:file system:(FAT32 or NTFS)

            >>Vista C:\

>Primary partition3:file system:(FAT32 or NTFS)

             >>A data partition common for XP and Vista.

PS:The above partitioning would be best accomplished in GParted....download and write it to a CD.....it recognizes all file systems......

---

### Post by meindian523 on 2007-10-29
What say,ppl?

---

### Post by meindian523 on 2007-10-29
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

There is the link to find out about GParted live CD and download it if you like what you see.....:)

---

### Post by mr_manson on 2007-10-29
I did it...

Then..

I installed Xp on 35 GB Primary
I installed Vista on 35 Gb Primary
I Make a Logical Extebded 50 Gb NTFS
so...after this

The free partition see by windows was 10 Gb 

I installed ubuntu 7.10 with a 

logical /boot 100 mb
logical /root 31996 mb
logical swap 2113 mb 

Thanks to all :guitar:


...i knew gparted but i didn't use cause i made an error with a correct number of primary and logical partiton...

:p

---

### Post by meindian523 on 2007-10-29
cool.......:guitar:

---

