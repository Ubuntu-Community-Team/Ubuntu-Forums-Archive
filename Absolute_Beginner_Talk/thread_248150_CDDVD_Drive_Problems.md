---
title: "CD/DVD Drive Problems"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by caimex on 2006-08-31
My CD/DVD drive partially stoped working all of a sudden. I'm quite sure it's not a hardware problem because the Ubuntu LiveCD works fine. Whenever I put any cd in nothing happens, I try double clicking the drive on places > computer but it says there is nothing in it. Also, when I try to burn a cd it just keeps saying that there is no cd in the drive.

I'm using the AMD64 version of Dapper if that makes a difference. I downloaded the ISO for the 32bit version because I'm not satisfied with the 64bit. I'm sure the cd's are not the problem either because the cd's that I'm trying that don't seem to be recognized I have used them before on the same install of Dapper.

Any help on how to fix this or troubleshooting would be greatly appreciated, I hope the 32bit version solves some if not all of the other problems I've been having. Thanks in advance. :D

---

### Post by catlett on 2006-08-31
Do you have 2 or one cd drives? When you go to Places<Computer<Filesystem<media what is the folder's name for the cdrom?
I am asking because I want to compare the mount point with the mount point /etc/fstab has. Enter ```
cat /etc/fstab
``` That will bring up the file for mountimg your devices. What is the mount point for your cd drive? (it will be /dev/hdc)
Are the 2 points the same?
I had this issue with playing dvd's. I have a dvd rom and a dvd writer. I put a dvd in the dvd writer and it wouldn't play. It said no media. I switched to the dvd rom and it worked. It seems xine (the media player I was using) was looking for /dev/hdd and the writer was /dev/hdc. Anyways the whole point is check /etc/fstab and see where it is mountimg the cd drive. It's a good place to start troubleshooting.

---

### Post by caimex on 2006-08-31
I only have one DVD/CD burner/drive or whatever the proper name is. Here is the output from cat /etc/fstab.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

The strange thing is that I once wrote a thread about this problem but right as I was about to post it, my drive suddenly recognized everything I threw at it. Thanks for the quick response. :)

---

### Post by catlett on 2006-08-31
I wish they were all solved that easily. Just in case you are new to ubuntu, I follow the Dapper Guide when setting up my multimedia etc. Just make sure to change the repository file which is /etc/apt/sources.list. It walks you through it but I just wanted to mention it because it is essential to using the guide. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
Take care

---

### Post by caimex on 2006-08-31
Hahhahahahah, made it work, checked the link you posted and found this command to manually mount it.

sudo mount /media/cdrom0/ -o unhide

And nce I run the command it recognizes anything I throw at it, whats the file that bash runs everytime I login or something like that to autorun that command? Thank you so much.

---

