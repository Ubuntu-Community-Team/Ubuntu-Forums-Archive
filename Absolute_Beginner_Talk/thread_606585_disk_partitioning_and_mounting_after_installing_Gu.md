---
title: "disk partitioning and mounting after installing Gutsy Gibbon"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by shahriar86 on 2007-11-08
Hi I am new to linux world as well as disk partitioning. While Dual-installing Gutsy Gibbon with xp I had this configuration

 /dev/sda1 C drive 7GB NTFS
 /dev/sda2 
 /dev/sda5 D drive 8GB NTFS
 /dev/sda6 E drive 8 GB NTFS
 unallocated 15 GB

I partitioned drive like this
first 

XP Part
 /dev/sda1 mounted as /media/sda1 7GB (This is actually my XP system Partition)
 /dev/sda5 mounted as /media/sda5 7.65GB
 /dev/sda6 mounted as /media/sda6 7.65GB

Ubuntu part (Allocating the unallocated free part)
 /dev/sda7 linux swap 512 MB
 /dev/sda3 ext3 mounted as root ( / ) 4.76GB
 /dev/sda4 fat32 mounted as /windows 10.04GB


After booting into Gutsy Gibbon
I can not access /dev/sda4

I want to remount /dev/sda4 to /media/sda4 so that I can write and read files on that partition.

Any suggestion how to remount my partition /dev/sda4 to /media/sda4

thanks

---

### Post by finer recliner on 2007-11-08
create a directory in /media called sda4

```
 mkdir /media/sda4 
```

then edit your fstab file as such: change the mount point for /dev/sda4 to the new mount point.

```
 gksudo gedit /etc/fstab 
```

restart the computer

---

### Post by finer recliner on 2007-11-08
oh wait, just to make sure we're all on the same page:

you won't find your files on your sda4 partition by navigating to /dev/sda4. you navagate your files by going to the mount point (/windows ) in your case.

try doing this:

```

cd /windows
ls
touch test.txt

```

in the above lines:
cd changes your directory,
ls will list what is in your current directory (your /windows partition)
touch will create a blank file called 'test.txt'. this is just to make sure you have permission to write to this location.

---

### Post by shahriar86 on 2007-11-08
umm... Finer seeing no response to my post for hours, I kinda messed up things a little bit more.

I used gParted to unmount /dev/sda4 from /windows and then reformat it into ext3 hoping that gPart will allow me mount it again. But unfortunately it does not and now I am stuck.

I followed your idea about---

mkdir /media/sda4

it now says mkdir: cannot create directory `/media/sda4': Permission denied

I also tried your second suggestion of editing fdisk file to remount /dev/sda4 to /media/sda4

it still shows /dev/sda4 mounted as /windows and fat32 system (although I have unmounted and formated it into ext3)_ see pic one

and unfortunately I cant change anything there. 
It says:
"Could not save the file /etc/fstab.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

please help me out.

---

### Post by shahriar86 on 2007-11-08
ok thanks anyway I am just going to do a fresh installation of gutsy gibbon again.

---

### Post by finer recliner on 2007-11-08
you need super user priveledges to edit most config files, that why you need to put the "gksudo" command infront of the gedit /etc/fstab. you may need to put "sudo" in front of the "mkdir /media/sda4" for similar reasons.

---

