---
title: "accessing itunes music through ubuntu"
date: 2011-06-29
forum: Apple Hardware Users
---

### Post by scotteik36 on 2011-06-29
there is an old thread that has a tutorial but i am having difficulty following the steps.

here is the tutorial:
[B]To do this, you will need to mount the OS X partition in Ubuntu.
Do this by adding a line to the /etc/fstab:

/dev/sda<whatever number partition OS X is - 2 for first partition normally> /mnt hfsplus defaults 0 1

Then, on the OS X partition go to your home directory , Get Info, and grant read permissions to everybody. That way Ubuntu has permission to access the music.

After that, in Ubuntu install the restricted extras (in add/remove programs). That way you can play back MP3/AAC files.

Finally, in rhythmbox (or whatever music player you use), add the directory /mnt/Users/<your user id>/Music/iTunes Music

That should do it. If you have songs purchased from the iTunes store, these won't play unless they're iTunes Plus tracks - blame the DRM for that.[/B]

my first problem is my /etc/fstab file is read-only. in order to add a line it needs to be read-write. How do i make the /etc/fstab file read-write?

next question:
i don't quite understand the partition number things. i am not to that point yet. but if anyone has an idea of how to specify or clear it up that would be great!

**/dev/sda<whatever number partition OS X is - 2 for first partition normally> /mnt hfsplus defaults 0 1**

again i am very new to linux so explaining things in laymens terms would be appreciated.

---

### Post by haqking on 2011-06-29
> **scotteik36 said:**
> there is an old thread that has a tutorial but i am having difficulty following the steps.

here is the tutorial:
[B]To do this, you will need to mount the OS X partition in Ubuntu.
Do this by adding a line to the /etc/fstab:

/dev/sda<whatever number partition OS X is - 2 for first partition normally> /mnt hfsplus defaults 0 1

Then, on the OS X partition go to your home directory , Get Info, and grant read permissions to everybody. That way Ubuntu has permission to access the music.

After that, in Ubuntu install the restricted extras (in add/remove programs). That way you can play back MP3/AAC files.

Finally, in rhythmbox (or whatever music player you use), add the directory /mnt/Users/<your user id>/Music/iTunes Music

That should do it. If you have songs purchased from the iTunes store, these won't play unless they're iTunes Plus tracks - blame the DRM for that.[/B]

my first problem is my /etc/fstab file is read-only. in order to add a line it needs to be read-write. How do i make the /etc/fstab file read-write?

next question:
i don't quite understand the partition number things. i am not to that point yet. but if anyone has an idea of how to specify or clear it up that would be great!

**/dev/sda<whatever number partition OS X is - 2 for first partition normally> /mnt hfsplus defaults 0 1**



again i am very new to linux so explaining things in laymens terms would be appreciated.

I cannot answer you directly so my apologies as i dont use a mac or itunes so this may be of no use to you. 
however similar questions have been posted before.

This can offer some food for thought
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

and there is numerous threads on here about it as well as the use of Wine or Virtual machines.

If this is completely off the mark for your situation then my apologies, just throwing some ideas your way ;-)

---

### Post by nzjethro on 2011-06-29
> **scotteik36 said:**
> 
my first problem is my /etc/fstab file is read-only. in order to add a line it needs to be read-write. How do i make the /etc/fstab file read-write?


You must use the "sudo" command to read and write system files like fstab. These system files are locked to regular users, so that you don't accidentally cook your system. You must login in as "root" (i.e. the "boss" user of the computer) to have read/write access to your system files, which is done by typing "sudo" (short for "superuser do") before your command. Try typing the following in a terminal:

```
sudo gedit /etc/fstab
```

Sudo logs you in, Gedit is the programme we'll be using to edit the file, and /etc/fstab is the file and location.

> **scotteik36 said:**
> 
next question:
i don't quite understand the partition number things. i am not to that point yet. but if anyone has an idea of how to specify or clear it up that would be great!


If you run:

```
sudo fdisk -l
```
(that's a lower case L), in a terminal, it will give you a list of your partitions. Try and find your OSX partition (by looking at the sizes). It should have something like **sda<some-number>** next to it. For example, my Windows partition is sda1, my Ubuntu partition is sda2. You can also open gparted by typing

```
gksudo gparted
```
then identify your OSX partition by looking at the size of the partitions and the amount of the partitions filled.

---

### Post by ajgreeny on 2011-06-29
> **nzjethro said:**
> You must use the "sudo" command to read and write system files like fstab. These system files are locked to regular users, so that you don't accidentally cook your system. You must login in as "root" (i.e. the "boss" user of the computer) to have read/write access to your system files, which is done by typing "sudo" (short for "superuser do") before your command. Try typing the following in a terminal:

```
sudo gedit /etc/fstab
```Sudo logs you in, Gedit is the programme we'll be using to edit the file, and /etc/fstab is the file and location.



If you run:

```
sudo fstab -l
```(that's a lower case L), in a terminal, it will give you a list of your partitions. Try and find your OSX partition (by looking at the sizes). It should have something like **sda<some-number>** next to it. For example, my Windows partition is sda1, my Ubuntu partition is sda2. You can also open gparted by typing

```
sudo gparted
```then identify your OSX partition by looking at the size of the partitions and the amount of the partitions filled.
Just a few points, but potentially important.

1.  For all applications with a gui you should not use sudo, but **gksu** if using gnome and **kdesu** for kde.  So do not use **sudo gedit** or **sudo gparted**, use **gksu** instead

2.  **sudo fdisk -l**, not **sudo fstab -l** for a list of all partitions.  You can use **sudo parted -l** as well for a different display of the same info.

See **Rootsudo** in my signature for all the details of why to do it this way.

---

### Post by nzjethro on 2011-06-29
> **ajgreeny said:**
> Just a few points, but potentially important.


Cheers ajgreeny, I've changed them in my original post. Sheesh, senior moment. ;)

---

### Post by scotteik36 on 2011-06-29
this information has been very informative and helpful! thanks!

unfortunately, i have not been able to gain access to my iTumes through ubuntu.

i have no idea what i am doing wrong and now whenever i start up ubuntu it i get a message saying it was having trouble accessing 
/mnt

here is my /etc/fstab:
[I]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=470b748c-9d35-4a8a-b3a3-314d71d0eefd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=557d8ceb-c0e7-44ef-8af9-17bfb8225a10 none            swap    sw              0       0
dev/sda4 /mnt hfsplus defaults 0 1[/I]

---

### Post by nzjethro on 2011-06-29
> **scotteik36 said:**
> 
here is my /etc/fstab:
...   
dev/sda4 /mnt hfsplus defaults 0 1

You have a small typo here. The line should read
```
[COLOR=red]**/**[/COLOR]dev/sda4 /mnt hfsplus defaults 0 1
```

I'm not sure if this would have caused that specific error. In my fstab, I have mounted it to the "/media" directory. What is the specific error message it is giving you?

Perhaps check whether /mnt is established. Run:
```
cd /
ls
```
and check whether "mnt" is in the list of directories it gives you.

---

### Post by scotteik36 on 2011-06-30
/mnt is there. the error message i get is at startup it says it is having trouble "mounting /mnt". then it gives me the option to skip mounting or retry.

also fixed that syntax error. nothing changed. I still don't have the correct permissions to get access to the files on my Macintosh HD partition.

i have tried navigating with the terminal and the GUI with no luck.

i feel like i am missing something.

---

### Post by pjd99 on 2011-06-30
What is the output from the following commands:
```

ls -la /dev/disk/by-uuid/

```and
```

sudo fdisk -l /dev/sda

```and is /mnt empty?
```

ls -la /mnt

```This should give us the information required to get the fstab entry fixed.

You can always try mounting it temporarily using Disk Utility.

---

### Post by scotteik36 on 2011-06-30
ls -la /dev/disk/by-uuid/  gives me this:

total 0
drwxr-xr-x 2 root root 120 2011-06-30 00:25 .
drwxr-xr-x 6 root root 120 2011-06-30 00:25 ..
lrwxrwxrwx 1 root root  10 2011-06-30 00:25 470b748c-9d35-4a8a-b3a3-314d71d0eefd -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-06-30 00:25 557d8ceb-c0e7-44ef-8af9-17bfb8225a10 -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-06-30 00:25 826A-0900 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-06-30 00:25 c98e1a49-4be0-3a05-8a2d-48cdd959413d -> ../../sda2



sudo fdisk -l /dev/sda
 gives me:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       17618   141306556   af  HFS / HFS+
/dev/sda3           17618       17618         977   ee  GPT
/dev/sda4           17618       19201    12717773+  83  Linux


ls -la /mnt
 gives me:

total 8
drwxr-xr-x  2 root root 4096 2011-04-21 11:50 .
drwxr-xr-x 22 root root 4096 2011-06-27 22:56 ..

---

### Post by pjd99 on 2011-06-30
Ahh, it was trying to mount your linux partition as the HFS+ one... 

Remove the following line from /etc/fstab:
```

*dev/sda4 /mnt hfsplus defaults 0 1*

```and replace it with:
```

UUID=c98e1a49-4be0-3a05-8a2d-48cdd959413d  /mnt hfsplus ro,defaults 0 2 
```then you should be able to drop to a terminal and perform
```

sudo mount /mnt

```This should mount it without having to restart.


```

ls -la /mnt
```will list the contents of the HFS partition after it's mounted.

From now on it should be there every time you power up.

If it mounts correctly, but you still cant access the files, you may need to do the following in the OSX terminal:
```

sudo chmod -R 755 Folder
```where "Folder" is the directory you want access to in Linux.

---

### Post by scotteik36 on 2011-06-30
mount: special device UUID=c98e1a49-4be0-305-8a2d-48cdd959413d does not exist


this is what i get from 
sudo mount /mnt

what does the long code refer to?

---

### Post by scotteik36 on 2011-06-30
whoops found a typo. forgot an "a". /mnt mount successful but still not getting the permission to access the music file....

edit:
did the chmod command from osx and it worked!!!!!!!! thank you so much!

---

### Post by pjd99 on 2011-07-01
> **scotteik36 said:**
> mount: special device UUID=c98e1a49-4be0-305-8a2d-48cdd959413d does not exist


this is what i get from 
sudo mount /mnt

what does the long code refer to?

You could have used /dev/sda2 instead of the long code, but...

The long code is the universally unique identifier for the partition. It is the preferred method of referencing drives in Ubuntu as it is possible for the /dev/sdX allocations to change between boots (it's happened to me - system gets rather confused). 

If you want to read further on it:
[COLOR=Blue][https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)[/COLOR]

---

