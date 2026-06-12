---
title: "Disk boot failure on dual boot system"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by TheOther on 2007-02-12
Hello,

I installed Ubuntu using 6.06 alternate i386 CD. On my system (256Mb, Athlon 1G, ASUSA7V, 30GB master + 120GB slave) was (and still is) a dual boot system of XP and ME on the master harddisk. 

The slave disk of 120GB is (intentionally) overwritten by Ubuntu installer. When I fire up the system it gives a "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER" (not to shout but it is in uppercase)

When I put the Ubuntu CD in the drive I can boot the system with the option 'Boot from first hard disk' presented by the CD.
Then I can boot the 'dual boot loader of XP and ME' or choose one of the (?) versions of the kernel.

How do I get grub from booting from hard disk without the CD?

---

### Post by nickoli_02 on 2007-02-12
I think the problem is you're booting from the MBR on the master disk which has XP and ME, but grub is on the MBR of the slave disk...

Try making the Ubuntu disk the master in the BIOS. Might work

---

### Post by phiphedog on 2007-02-12
Perhaps you don't have the windows disk set as bootable. You can do this through Qparted on the ubuntu installation disk. Just go through the motions as if you were installing ubuntu and when you get to the screen about partitioning your hard disk, select "manually partition my hard disk" and then you should be able to right click the windows partition and make it bootable and then exit Qparted and restart.

---

### Post by TheOther on 2007-02-12
The system uses IDE hard disk that are master / slave via jumpers. I think i mess up the C: drive logic is I switch the master - slave settings. Is't it?

---

### Post by TheOther on 2007-02-12
> **phiphedog said:**
> Perhaps you don't have the windows disk set as bootable. You can do this through Qparted on the ubuntu installation disk. Just go through the motions as if you were installing ubuntu and when you get to the screen about partitioning your hard disk, select "manually partition my hard disk" and then you should be able to right click the windows partition and make it bootable and then exit Qparted and restart.

I did a text install.So I did it again to the partionioning part. The information I got:
Use as: FAT 32 file system
Mount point: /media/hde1
Mount options: defaults
Bootable flag: on

Use as: ntfs
Mount point: /media/hde5
Bootable flag: off

Use as: fat 32 file system 
Mount point: /media/hde6

Use as: Ext3 journaling filesystem
Mount point: /media/hdf1
Mount options: defaults
Bootable flag: on

So in order: ME system, XP system, data partition, Ubuntu. The are two partitions with boot flaf on??? Any suggestions?

---

### Post by dannyboy79 on 2007-02-12
this had happened to me also. I believe I solved it by removing the boot flag from the partition (ubuntu hard drive) as well as making sure your #groot line is correct within your /boot/grub/menu.lst file.

i'll paste what I had written within a thread I started after geek_man suggested the solution.

WOW, i have no idea why my menu.lst would have changed in the first place but that was it!!!! so now I have # groot=(hd2,1) and it works! YEAH! God, i thought for sure I'd have to mess around and either backup everything up then put it back onto a newq drive or something more serious. I am so glad to have Ubuntu back! I missed her. I was out for more than a week! I played with a little each day for most days, some days didn't but 7 days without Ubuntu isn't fun!!! thanks to everyone for there help!!!!! The super grub disk couldn't even fix this. I wonder if I should tell the creator of the program that the #groot line should be looked at if all else fails.

now I know I didn't document it above within that post but I know I turned off hte boot flag using super grub disk when I was trial and error'ing over and over to get my system to boot. I was getting the same exact error you're getting. good luck

---

### Post by TheOther on 2007-02-13
> **dannyboy79 said:**
> this had happened to me also. I believe I solved it by removing the boot flag from the partition (ubuntu hard drive) as well as making sure your #groot line is correct within your /boot/grub/menu.lst file.

i'll paste what I had written within a thread I started after geek_man suggested the solution.

WOW, i have no idea why my menu.lst would have changed in the first place but that was it!!!! so now I have # groot=(hd2,1) and it works! YEAH! God, i thought for sure I'd have to mess around and either backup everything up then put it back onto a newq drive or something more serious. I am so glad to have Ubuntu back! I missed her. I was out for more than a week! I played with a little each day for most days, some days didn't but 7 days without Ubuntu isn't fun!!! thanks to everyone for there help!!!!! The super grub disk couldn't even fix this. I wonder if I should tell the creator of the program that the #groot line should be looked at if all else fails.

now I know I didn't document it above within that post but I know I turned off hte boot flag using super grub disk when I was trial and error'ing over and over to get my system to boot. I was getting the same exact error you're getting. good luck

I did change the boot-flag of the slave (ubuntu) harddisk to 'off'. The #groot line was ' #groot=(hd1,0)' . This looks logical to me. I changed it to (hd2,1) but nothing happend.
When I changed the bootflag (I used the ubuntu install alternate disk) the partitioner complained not having a root system ?????
I can still boot from CD and access XP/ME and ubuntu.
I looked on the first harddisk in the boot sector and I could not find the message ' DISK BOOT FAILURE...'. So where does this come from? (I read the first sectors in DOS using debug command.)
I read in your message ' super grub disk' . Is this something I can try? Any suggestions?

---

### Post by dannyboy79 on 2007-02-14
well, the first we need to clarify is what drive is the first boot device in your bios???
if it's the one that has me and winxp on it, and you DIDN'T overwrite the mbr of this drive, and you want to dual boot using winxp's boot loader than you need to follow this:
[http://www.hccfl.edu/pollock/AUnix1/DualBoot.htm#WinBL](http://www.hccfl.edu/pollock/AUnix1/DualBoot.htm#WinBL)

if you wanted to dual boot using grub, than during the install you told grub where it should install itself, if you chose hd4 which would mean it got installed on your hde drive's mbr, this will cause Linux to boot instead of XP the next time your computer boots from the hard disk. BUT since your groot line isn't correct, grub doesn't know where to find your menu.lst file so you need to fix that. Your #groot line defines the root grub partition. so it's where ever grub was installed. mine is (hd2,1) because I installed grub on the hard drive defined in ubuntu as hdc and it's on the first partition (i created a boot partition, where many people do not, so it would've been hd2,0). see what I mean. you showed me your fdisk -l and it appears as though your ubuntu install is on hdf1, so if you didn't create a boot partition, than grub's folder was created within the boot folder on the same partition as your root partition. if that's the case, your #groot line would need to be (hd5,0). now I don't know if your system ever worked but mine did and then one day my #groot line within my menu.lst file was changed for no reason so that's why I am telling to check that out. it appears to me that yours is wrong based on what you have informed me of. hopefully if you change it to what I have suggested than it should boot.

---

### Post by dannyboy79 on 2007-02-14
yes, change your #groot line to hd5,0 and you should be set. what has happened is that your mbr was overwritten by grub but grub can't find where grub is installed or your menu.lst. unless you actually created a boot partition like I did, which made my groot line hd2,1 because I installed grub's files on ubuntu's hdc drive and it's first partition (boot partition). good luck

EDIT: i don't know what has happened here. i thought I had posted the above post, then when I did a refresh it wasn't there, so I thought my entire post got deleted some how so I created another quick one, which is this one, which now I see isn't needed. sorry for those who get emails eash time this is updated.

---

### Post by TheOther on 2007-02-15
> **dannyboy79 said:**
> yes, change your #groot line to hd5,0 and you should be set. what has happened is that your mbr was overwritten by grub but grub can't find where grub is installed or your menu.lst. unless you actually created a boot partition like I did, which made my groot line hd2,1 because I installed grub's files on ubuntu's hdc drive and it's first partition (boot partition). good luck

EDIT: i don't know what has happened here. i thought I had posted the above post, then when I did a refresh it wasn't there, so I thought my entire post got deleted some how so I created another quick one, which is this one, which now I see isn't needed. sorry for those who get emails eash time this is updated.

Thank you dannyboy79 to try helping me. I tried many things untill ubuntu wasn't booting anymore. Then I searched for super grub disk. This convinced me that to boot sector was ok. But the system was not starting up from harddisk. (And ubunto was scrambled up.) I took a dive into the bios and disabled almost everything. (Until now the most things where on 'auto'.) I reinstalled ubuntu and... It works! 

Many thanks to keep me on going. Now I even have a 'super grub disk'. My ubuntu adventure can start now.

(I only can guess what was wrong: I think some auto settings about SCSI drive that are now disabled got in the way????)

---

### Post by dannyboy79 on 2007-02-15
just a word of advice though, anytime you get yourself in trouble or something doesn't work I strongly suggest next time you work through it using our help instead of re-installing. you won't learn anything by simply re-installing everytime you get in trouble. just some advice is all.

---

