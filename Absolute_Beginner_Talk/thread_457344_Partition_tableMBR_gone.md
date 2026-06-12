---
title: "Partition table/MBR gone"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Southbound on 2007-05-28
I have a laptop that originally had ubuntu, windows xp, and swap partitions.  I was trying to unallocate space from the windows partition to make room for a new shared partition, when something went wrong.  I wasn't in the room when it happened, but I came back to a grub "error 17."

Right now I'm using the ubuntu live cd.  Running the command "sudo fdisk -l" I get:

> Disk /dev/sda: 30.0 GB, 30005821440 bytes
240 heads, 63 sectors/track, 3876 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2003    15142648+   7  HPFS/NTFS
/dev/sda2            2710        3876     8819685    5  Extended
/dev/sda5            2710        3743     7807558+  83  Linux
/dev/sda6            3743        3876     1012063+  82  Linux swap / Solaris


I can see the contents of the windows partition as "disk" with nautilus, but the linux partition is not accessible.  I get an error when I try to mount the linux partition.  When I open up GParted or use the live cd installer it shows the entire disk as unallocated.  Also notice in the fdisk readout the extended partition seems to occupy the same blocks as the linux and swap partitions. 

Is there a way to restore my partition table/mbr?  If necessary I can burn the linux partition but I'd like to keep windows intact if possible.  Thanks.

---

### Post by Southbound on 2007-05-28
Exciting update:  I found this program "gpart" that claims to be able to fix partition tables. [http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)

However I have no idea how to make it usable.  It comes as source code or a "statically linked linux binary."  I downloaded the binary but I can't figure out how to run it.  Navigating to its directory and typing "gpart" yields:

> The program 'gpart' is currently not installed.  You can install it by typing:
sudo apt-get install gpart
Make sure you have the 'universe' component enabled
bash: gpart: command not found

I have no idea what the universe component is.  I typed "sudo apt-get install gpart" and got: 
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gpart is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gpart has no installation candidate


I tried making a directory on the desktop "geepart" and typing the command "sudo install gpart -t /home/ubuntu/Desktop/geepart."  This copied the original gpart file to the new directory I made, but when I tried to run it from there it gave me the original "has not been installed" message.


Any suggestions anyone?

---

### Post by odiseo77 on 2007-05-28
I haven't used this program, but it seems you're not executing it properly. First, you should start by giving it execution permissions:

```
chmod +x gpart.linux
```

Then execute it with the following command:

```
./gpart.linux [options] /dev/sda
```

---

### Post by dstew on 2007-05-28
Southbound:

Regarding your original post, what error message do you get when trying to mount your linux partition? And what mount command are you using? Remember, you have to create a mount point before mounting a file system.

Also, any extended partition (number 2 in your case) by definition will "contain" the logical partitions with numbers 5 and up, so there is nothing wrong with your fdisk output that I can see. I don't think anything is wrong with your partition table. You might have a grub installation problem though.

---

### Post by Southbound on 2007-05-28
Odiseo77:  Thanks a lot, those commands got that program working.  I just didn't know what I was doing.  I'll post here if it yields anything helpful.

dstew:  I tried using the command "sudo mount -t ext3 /dev/sda5 /media/Ubuntu,"  I also tried mounting it to different directories and I tried using "vfat" instead of "ext3."  I've played around with mount a lot, and in all cases I got the following error:

> mount: wrong fs type, bad option, bad superblock on /dev/sda5,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

The attached screen shot is one of the reasons I think it might be the partition table.  Thanks for all the help so far.

---

### Post by dstew on 2007-05-29
OK, you are right, there is something wrong with that partition. Have you run **fsck /dev/sda5** yet to check the filesystem?

You are also right that **gpart** is probably the way to go to try to recover. You can install it on your Live CD booted system using Synaptic. You have to enable the Universe repository in the Settings tab of Synaptic, then search for gpart. (Note: if you search for gpart, it will also show you gparted, but of course you already have that). Install gpart on your Live CD-booted system, and you can use it from there. It will, of course, disappear when you shut down, but hopefully you will be able to fix your disk.

---

### Post by Southbound on 2007-05-29
Alright, I got it fixed using gpart that I downloaded from the web and the commands listed by odiseo77.  After I fixed the partition table with gpart I got a grub error 22 and had to reconfigure grub, but that went smoothly.  Gpart worked great and I recommend it to anyone with a similar partition table problem.  I guess when I tried to change the partitions around using a windows partition manager program something just went wrong somewhere and I ended up with no partition table.

Thanks a lot for all the help everyone!

---

