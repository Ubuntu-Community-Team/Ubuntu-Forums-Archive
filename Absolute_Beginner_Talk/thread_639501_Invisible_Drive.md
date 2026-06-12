---
title: "Invisible Drive"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Gazz777 on 2007-12-13
Hi, I have now been using Ubuntu for a week :)

There is the odd thing, for instance it cant see my 320gig spare drive, I have a dual boot system in my Sata 300gig drive, partitioned, so this isn't a priority,

My music and video's are on the 320 gig drive, so if I want to listen or view I must reboot and go into Windows ( pain in the ! )


gary@Linuk-DeskTop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=84e97a57-af0d-498f-9002-0da15958fbf1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8E546B64546B4E51 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=5288979288977369 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=49179bb9-d6f3-46cb-a87f-c177eb1c93c1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
gary@Linuk-DeskTop:~$ 

Any help will be appreciated.
Still finding it a little weird, everything is free :guitar:

Kind Regards
Gary

---

### Post by mcduck on 2007-12-13
Could you post the output of running 'sudo fdisk -l' as well? That will list all your drives and partitions (not only those that are already configured in Ubuntu. With that information and the contents of fstab that you already posted we should be able to help you to add the 320GB drive into fstab.

And yeah, post the output of 'blkid' as well so we can get the UUID's for those partitions as well..

---

### Post by adamite on 2007-12-13
Did you try mounting the drive? I bet if you mount that, you will see your files there and you should be able to play your music, etc.:)

---

### Post by Gazz777 on 2007-12-13
gary@Linuk-DeskTop:~$ blkid
/dev/sda1: UUID="8E546B64546B4E51" TYPE="ntfs" 
/dev/sda5: UUID="84e97a57-af0d-498f-9002-0da15958fbf1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="5288979288977369" TYPE="ntfs" 
/dev/sda7: UUID="49179bb9-d6f3-46cb-a87f-c177eb1c93c1" TYPE="swap" 
gary@Linuk-DeskTop:~$ 



sudo fdisk -l
All I get from this command is

>

does the above help any ?

Thanx

---

### Post by Gazz777 on 2007-12-13
> **adamite said:**
> Did you try mounting the drive? I bet if you mount that, you will see your files there and you should be able to play your music, etc.:)

Any pointers on how I mount the driv ?:confused:


:confused::confused::confused:

---

### Post by viking777 on 2007-12-13
Search the forum for the word 'mount'?

Or would you like us to pop round and mount it for you?

---

### Post by Gazz777 on 2007-12-13
> **viking777 said:**
> Search the forum for the word 'mount'?

Or would you like us to pop round and mount it for you?

Sharp

err thanx

---

### Post by mcduck on 2007-12-13
> **Gazz777 said:**
> gary@Linuk-DeskTop:~$ blkid
/dev/sda1: UUID="8E546B64546B4E51" TYPE="ntfs" 
/dev/sda5: UUID="84e97a57-af0d-498f-9002-0da15958fbf1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="5288979288977369" TYPE="ntfs" 
/dev/sda7: UUID="49179bb9-d6f3-46cb-a87f-c177eb1c93c1" TYPE="swap" 
gary@Linuk-DeskTop:~$ 



sudo fdisk -l
All I get from this command is

>

does the above help any ?

Thanx
Now that's strange. 'sudo fdisk -l' should do something like this:
```
sudo fdisk -l
[sudo] password for mcduck:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbcdb4851

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        3430    25599577+   c  W95 FAT32 (LBA)
/dev/sda3            3431        5980    20482875   83  Linux
/dev/sda4            5981        9729    30113842+   5  Extended
/dev/sda5            9539        9729     1534207+  82  Linux swap / Solaris
/dev/sda6            5981        9538    28579572   83  Linux
```

And even the blkid should actually show the 320GB disk.

How is the disk connected? With SATA? Do you have some RAID controller on your motherboad? If the disk is connected through one that isn't supported in Linux that could be causing the problem..

---

### Post by leader303 on 2007-12-13
edit edit forget about it.
saw a typo where there was none.

---

### Post by mcduck on 2007-12-13
Oh. It's 'sudo fdisk -l', with a small L, not a big i or the pipe character (|).

I tried it and the only way I could get result like that for fdisk was when I tried with the pipe in the end of the command.

But that still doesn't explain why blkid doesn't show the drive. :/

---

### Post by Gazz777 on 2007-12-13
> **mcduck said:**
> Oh. It's 'sudo fdisk -l', with a small L, not a big i or the pipe character (|).

I tried it and the only way I could get result like that for fdisk was when I tried with the pipe in the end of the command.

But that still doesn't explain why blkid doesn't show the drive. :/


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1afa1af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38912   210162330    f  W95 Ext'd (LBA)
/dev/sda5           12749       16152    27342598+  83  Linux
/dev/sda6           16573       38912   179446018+   7  HPFS/NTFS
/dev/sda7           16153       16572     3373618+  82  Linux swap / Solaris

Partition table entries are not in disk order
gary@Linuk-DeskTop:~$ 


Thanx mcduck I hope you can make some sense out of this.

kind regards
Gary

---

### Post by viking777 on 2007-12-14
Do you have gparted installed?

If so could you fire it up and see what drives it can find (look in the drop down box top right when the program has loaded).

If you haven't got it you can find it in the repositories and it is very useful to have around.

Couple of other questions. Is the drive internal or external? What is it formatted as Fat32, NTFS? lastly can I just confirm that the drive is fully visible to windows.

---

### Post by Gazz777 on 2007-12-14
> **viking777 said:**
> Do you have gparted installed?

If so could you fire it up and see what drives it can find (look in the drop down box top right when the program has loaded).

If you haven't got it you can find it in the repositories and it is very useful to have around.

Couple of other questions. Is the drive internal or external? What is it formatted as Fat32, NTFS? lastly can I just confirm that the drive is fully visible to windows.



I haven't as yet got gparted installed, I formatted (NTFS)whole of the 300+gig hard drive (sata) I then used the windows disc to create partitions, which wasn't't easy as Ubuntu didn't't seem to see them, however eventually I managed it, I have one partition at 100gig (windows ) another 30 gig ( Ubuntu ) 170 gig as storage, I also created a drive for storage, unsure about this one Ubuntu said it needed storage or swap.

My spare drive can be seen in windows without any problem, ( Internal, NTFS, )

Can a Bios setting perhaps be out, it is a new PC 2 weeks old.
One week with Linux ! :confused:

Thanx for your time, appreciated.

Gary

---

### Post by viking777 on 2007-12-14
If it were a bios problem then I don't think you would see it in windows either - after all,the bios is the same whatever os you are using.

Strange one this, external hard drives not showing up, not unusual, but internal ones not showing:confused:

I'll think about it but I don't I don't think I am going to come up with an answer.

If you haven't got gparted then I wouldn't worry too much, I don't think it will tell you anything that fdisk didn't (I just have this inbuilt prejudice against using command line tools when there are perfectly good graphical ones out there that are much easier to use and understand).

---

### Post by viking777 on 2007-12-14
Ok just had another thought. 

You specify that the drive that is seen is a sata drive. Could it be that the other drive is pata? 

If that is the case you might like to read through this thread:

> [http://ubuntuforums.org/showthread.php?t=637776](http://ubuntuforums.org/showthread.php?t=637776)

Hope that helps.

Edit. or this one.

[http://ubuntuforums.org/showthread.php?t=608368](http://ubuntuforums.org/showthread.php?t=608368)

---

### Post by Gazz777 on 2007-12-14
> **viking777 said:**
> Ok just had another thought. 

You specify that the drive that is seen is a sata drive. Could it be that the other drive is pata? 

If that is the case you might like to read through this thread:



Hope that helps.

Edit. or this one.

[http://ubuntuforums.org/showthread.php?t=608368](http://ubuntuforums.org/showthread.php?t=608368)

Pata,  Western Union 320 gig

Thanx for the thread redirect, doesn't look good, will live with this for awhile, I assume if I bought another 300gig Sata all will be well ?

Have ordered a couple of books on Ubuntu but there still to appear.

Appreciate your help..............

Regards
Gary

---

### Post by viking777 on 2007-12-14
There are several bugs on launchpad that deal with the mixed sata/pata environment, so it does seem to be something that Ubuntu has difficulty with.

But please, do not go out and buy new disks on my say so, I don't know enough about it.

---

