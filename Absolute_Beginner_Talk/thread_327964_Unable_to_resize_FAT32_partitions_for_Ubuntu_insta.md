---
title: "Unable to resize FAT32 partitions for Ubuntu install"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2006-12-30
I did a search and read a lot of post on partitioning but didn't find anything like my problem. Here is what I have, 2 HDD and 2 opticals.

HDa Seagate 160GB divided into 5 partitions IDed in Windows as:
C:\ 4.66GB this has Win 98 on it and is the primary boot drive 3.86GB free. FAT32
The rest are logical drives in an extended partitions:
E:\ 36.1GB Apps and some critical data 34.4GB free FAT32
F:\ 36.1GB Apps and data 16.2GB free FAT32
G:\ 36.1GB mostly backup for the other HD 21.2GB free FAT32
H:\ 36.0GB Apps 34.0GB free FAT32

HDd Maxtor 80GB with 6 partitions
D:\ 7.59GB Apps and data 4.96GB free FAT32 primary 
the rest are logicals in an ext patition
I:\ 243MB Windows temp file and odds 'n' ends 229MB free FAT16
J:\ 17.1GB data 15.4GB free FAT32
K:\ 17.2GB data 15.5GB free FAT32
L:\ 17.1GB data 10.2GB free FAT32
M:\ 17.1GB data and some backups for the other drive 4.38GB free FAT32

I would like to install Ubuntu on either drive G:\ or H:\. 

I have the Live CD 6.10 and when I tried installing, the partition applet (Gparted Partiton Editor) failed during a resize of these (and other) partitions. I get the error "Partitions Failure" "file system is reporting free space as 0 clusters not 2012475 clusters." I tried using the partition app alone outside the install program. I even tried resizing partition D:/ since it is not in an ext partition, but that failed, too, giving a message that the files system reported (I forget the exact numbers) 13,xxx,xxx,xxx clusters not 130,xxx,xxx clusters. 

I'm not sure how to proceed at this point. I have ran ScanDisk and defragged all the partitions from Windows. I am hesitant to try the alternative CD since I am totally unfamiliar Linux commands. Any help is much appreciated.

---

### Post by smoker on 2006-12-30
not 100% sure, but i think you have to install ubuntu in a primary partition if you want it to be bootable. why do you need so many partitions if you don't mind me asking?

---

### Post by jvc26 on 2006-12-30
You have to install to a primary partition. The use of the alternate CD does not require commands, it is just a text based interface rather than a GUI - i.e. you load the cd on boot, then run through step-by-step commands to get it installed - the same steps as you do on the live cd install just in text rather than GUI. The other thing is, have you done the md5 checksum on your cd and have you checked it for errors? (Just in case there is an error with the cd you are trying to install from) And finally, is there any reason for the huge number of partitions - couldnt you just reorganize your entire HDD to have 1 disk windows and 1 ubuntu or 1 and a half windows and half ubuntu instead of having the huge number of partitions you have?
Il

---

### Post by louieb on 2006-12-30
Linux can be installed in a logical partition. If it were mine I would get the GParted live CD and:[LIST]
[*]Delete the h: partition.
[*]add 2 logical partitions in the now unallocated space
[*]1 swap about the size of physical memory or a little larger
[*]2. the partition to install Ubuntu Linux. (format ext3)
[*]Now boot to the Install CD and when it asks choose manual partitioning
[*]point it to your new partitions[/LIST]I think you get the idea. got to go to work. Good luck.

---

### Post by rajeev1204 on 2006-12-30
hmm

who says it has to be instaled in a primary partition?/

mine is totally on logical partition including home ,swap and whatever else.


I too had issues with auto partition so i did a manual install on my D partition(logical

read more about this before installing

try this [www.psychocats.net](www.psychocats.net) and [www.ubuntuguide.org](www.ubuntuguide.org)


regards

rajeev

---

### Post by Patrick K on 2006-12-30
I might be able to delete the H: partition then remake it smaller then copy the apps back using the unallocated space for Linux. I have about 60 apps that run from that partition, and you may know what a pain Windows can be if you move anything. Many of these apps are no longer available so reinstalling them ain't gonna happen. They have to be on that partition. 

All these partitions go back many, many years (this is the original W98 installation done in 1998, I've never had to reinstall, this system runs smooth as silk (most of the time, the few times it hasn't I've be able to fix it)). When I installed these two drives last year, I kept the partition structure to keep Windows happy. I have hundreds of shortcuts spanning all these drives. 

One more question: Windows will completely ignore both the Linux ext3 partition and the Linux swap partition, correct?

---

### Post by rajeev1204 on 2006-12-30
YES

windows does not recognise that .U can share FAT 32 with linux and windows as linux can read and write to fat 32.

NTFS sharing not recommended and not safe .(I think it is experimental yet)

Is ur hard drives in a raid array? I think that has to be looked at during install .

Iam not sure, but i have read somewhere about how to install when having RAID . I have only single harddrive so it was simpler for me. I completely dedicated C for windows and used half of D for ubuntu. The remaining half i later shared with windows using some guides here.

Luckily , ubuntu recognised my windows partition and i got dual boot.

U seem to have a lot many partitions so iam not sure how to do the install. Also a defrag is recommended before installing Ubuntu.

I cannot help any further

Please do more reading in these forums or ask for more help 


good luck

rajeev

---

### Post by Sef on 2006-12-30
> I am hesitant to try the alternative CD since I am totally unfamiliar Linux commands. Any help is much appreciated.
Edit/Delete Message

Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for learning how to install using the alternate cd.

---

### Post by Patrick K on 2006-12-30
SUCCESS!!!

I have Ubuntu successfully up and running. I backed up the H: drive then deleted the partition. Using the Live CD, I recreated a FAT32 partition, leaving 10GB unformatted. Next I created a EXT3 partition and a 750MB swap partition. After that the install went pretty smooth. I got notices that nearly all the FAT32 drive had errors (Windows' ScanDisk didn't find any) so I clicked continue. Widows is working fine after moving all the files back and Linux seems to be doing well, too. I'm posting from the new install. Now, I just need to learn how to use it. Grub is working correctly, too.

Thanks to all for your help.
Patrick

---

