---
title: "Partitions recomendation?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by sab0403 on 2007-07-05
Well, since my data partition [will probably go kaput]("http://ubuntuforums.org/showthread.php?t=493117"), I'm going to delete it, reformat, and copy all the files back. I have some questions, however:

1) Currently I have a (primary) ext3 partition, and then the NTFS (the one being destroyed) under an extended partition. Do I still need the extended partition? Or can I just erase it and add another primary?

2) What's the best filesystem for this one? I'd like to share files with Windows *ocasionally*, but I can just run Samba for that. However I *might* want to install a windows partition on that PC down the line, so I'd like for that partition to be at least readable by Windows (natively or with utils, I don't mind). Is ext3 readable within a Windows OS? Or do I have to stick with some flavor of FAT?

3) If I end up with 2 ext3 partitions, will Ubuntu see them as it does now, as the "File System" and a separate volume (sda#), or will it see it as an entire "File System"? I ask because if I switch to ext3, I most definitely want my home directory to reside there, and it would be cumbersome if Ubuntu sees it as another volume...

Anyway, I look forward to your thoughts. Thanks!

---

### Post by sab0403 on 2007-07-05
*bump*

---

### Post by Cypher on 2007-07-05
1) You can have up to 4 primary partitions. If you want to have more than 4 partitions in general, you'd have to make 3 of them primary, the 4th an extended and all subsequent partitions logical partitions within that extended partition.

2) Windows can access EXT3 using FS-Driver. Linux can acess NTFS using NTFS-3G. So I guess this one is really up to you..:)

3) If you are not re-install your existing Ubuntu, your current EXT3 partition will continue to perform it's duty. Ubuntu will know about the next EXT3 partition, but unless instructed to by the /etc/fstab file, it will not mount it anywhere..

---

### Post by bren on 2007-07-05
1) you can have max of 4 primary.   sounds like you are combining 2 paritions as you change things so maybe your new no of partitions is 4 or less.  if so you kno longer need extended.....otherwise you do

2) yes ext3 is readable by windows if you install a small utility (search for it)

3) ubuntu will see all the partitions.   look in /dev/ for where the drives are and mount as you want eg 

mount -t ext3 /dev/sda1 /media/sda1

hope that helps

bren

---

### Post by apunc1 on 2007-07-05
I don't know about #1

2. ntfs-3g   llows you to both read from and write to NTFS partitions from Ubuntu.
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

FS Drive  small program that allows Windows to read from and write to Ext3 partitions.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

3. It will mount them according to mount points. for example /  and /home are both ext3 but / will be mounted as the boot partition for ubuntu and /home as the home partition for settings and data. I'm not sure if this is what you mean.

---

### Post by sab0403 on 2007-07-05
Thanks for the replies.

Ok, so I have to add it to fstab once I make it, right? I'm thinking I'm going to go with an ext3.

Now, what should I use to erase/create my partition? I used Partition Magic back in Windows, but I'm clueless in Linux.

I need to be able to erase that partition without touching the other, since now I'm holding the data in the boot partition. Can I do that?

---

### Post by apunc1 on 2007-07-05
> **sab0403 said:**
> Thanks for the replies.

Ok, so I have to add it to fstab once I make it, right? I'm thinking I'm going to go with an ext3.

Now, what should I use to erase/create my partition? I used Partition Magic back in Windows, but I'm clueless in Linux.

I need to be able to erase that partition without touching the other, since now I'm holding the data in the boot partition. Can I do that?

download gparted or use the partition tool in feisty live cd.

---

### Post by Cypher on 2007-07-05
Or go the command like route with "mke2fs", do a "man mke2fs" for details..

---

### Post by sab0403 on 2007-07-05
Gparted... looks good.

I checked mk2fs, but it apparently only *creates* an ext3 filesystem... it doesn't delete another partition.

How would I go about that in the command line?

---

### Post by Cypher on 2007-07-05
"man fdisk"..:)

---

### Post by moredhel on 2007-07-05
^ lol

ew. fat. fat32 (even more fat ;) )

I would go for all out ext3, and just install the drivers for windows...

I used to have ext3 for linux, ntfs for windows, fat32 for documents/music/etc for both. But fat32 has **** permissions and lots of other bad things about it, probably because it's outdated now, as i'm sure it was good when it came out. (well actually no because it's m$ ;)

I found the simplest way was to get a 60gb 3rd harddrive and make it ext3, then have it mounted as /home in linux, and as F [documents] in windows. That way I can be lazy when i reinstall ubuntu and windows (install on entire disk :D )

EDIT: so for example I ended up as:

80gb linux ext3 (windows as z:) (linux as /)
60gb documents ext3 (windows as F:) (linux as /home)
120gb windows ntfs (with ext3 drivers installed) (windows as c:) (linux as /media/windows)

That worked out real well. But then i threw out windows and just has 120 as / and 80 as /home :)

---

### Post by stchman on 2007-07-05
> **sab0403 said:**
> Well, since my data partition [will probably go kaput]("http://ubuntuforums.org/showthread.php?t=493117"), I'm going to delete it, reformat, and copy all the files back. I have some questions, however:

1) Currently I have a (primary) ext3 partition, and then the NTFS (the one being destroyed) under an extended partition. Do I still need the extended partition? Or can I just erase it and add another primary?

2) What's the best filesystem for this one? I'd like to share files with Windows *ocasionally*, but I can just run Samba for that. However I *might* want to install a windows partition on that PC down the line, so I'd like for that partition to be at least readable by Windows (natively or with utils, I don't mind). Is ext3 readable within a Windows OS? Or do I have to stick with some flavor of FAT?

3) If I end up with 2 ext3 partitions, will Ubuntu see them as it does now, as the "File System" and a separate volume (sda#), or will it see it as an entire "File System"? I ask because if I switch to ext3, I most definitely want my home directory to reside there, and it would be cumbersome if Ubuntu sees it as another volume...

Anyway, I look forward to your thoughts. Thanks!

1.  No, if you are doing a complete hdd wipe then make a partition for Ubuntu of abour 30G and the rest for storage.

2.  I recommend you install XP/Vista first.  M$ want to be the boss of your system.  If you want to share a partition with WIndows then I recommend FAT32 (vfat).  Both Linux and Windows will be able to read/write no problem.

3.  Ubuntu will see each partition as a sda# or hda#.

---

### Post by sab0403 on 2007-07-05
fdisk! Alright, I'l give it a go.

Thanks again!

---

### Post by sab0403 on 2007-07-05
The thing is, I'm not using a desktop - this is a laptop. So adding another HD is out of the question.

I have a 100Gb HD, and currently I have a 25 Gb partition for Ubuntu, and the rest for storage. I'm going to delete that storage partition (currently NTFS) and then create it again (this time as ext3).

Also, how do I tell Ubuntu I want a certain directory on the data partition to be my /home directory?

---

### Post by stchman on 2007-07-05
> **sab0403 said:**
> The thing is, I'm not using a desktop - this is a laptop. So adding another HD is out of the question.

I have a 100Gb HD, and currently I have a 25 Gb partition for Ubuntu, and the rest for storage. I'm going to delete that storage partition (currently NTFS) and then create it again (this time as ext3).

Also, how do I tell Ubuntu I want a certain directory on the data partition to be my /home directory?

Ubuntu places your /home folder in the partition it installs itself.  There are post install methods to place the /home folder in another partition.

---

