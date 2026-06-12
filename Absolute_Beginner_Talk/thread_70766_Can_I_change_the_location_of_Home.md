---
title: "Can I change the location of Home?"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by Vulpus on 2005-10-01
On MS Windows you can easily change the location of 'My Documents' to another folder or drive.  In my case i have changed it to D:\DATA so that all my data (my docs, my pictures, my music etc) is saved on a seperate partition.

Can you do the same thing with the 'Home' folder in Ubuntu?  At the moment the Home folder is on the Linux partition on  HDA1 but I would like to move it to HDB1 (which is a FAT32 partition).

---

### Post by Leif on 2005-10-01
yes. copy all your files over to the new home, and then mount the new partition as home. in my case, it looks like this in /etc/fstab :

```
/dev/hda7       /home           ext3    defaults        0       2

```

obviously, you need to change it to reflect fat32, so probably something more like :

```
/dev/hdb2       /home           vfat    umask=000      0       0

```

---

### Post by mal on 2005-10-01
[QUOTE=Leif]yes. copy all your files over to the new home, and then mount the new partition as home. in my case, it looks like this in /etc/fstab :
```
/dev/hda7       /home           ext3    defaults        0       2

```
obviously, you need to change it to reflect fat32, so probably something more like :
```
/dev/hdb2       /home           vfat    umask=000      0       0

```[/QUOTE]
Just remember that your home folder holds much more than documents - it holds your personal settings for most applications (in hidden folders).
Also remember to preserve permissions when copying - use the "-p" option with the cp command.
Mal

---

### Post by GTvulse on 2005-10-01
Don't try to run your home partiton off a FAT32 filesystem. The latter does not provide support for access permissions not data integrity as EXT3 or ReiserFS would. OTH, a FAT32 filesystem works nicely as a data exchange space in a Windows/Linux dual boot system.
On the issue of moving your home directory, you need to be careful if you don't want to lose data. A strategy that works for me:
[list=1]
[*] Boot in single user mode, aka recovery mode. You will be root at this point, therefore there is no need to type "sudo" at every step.
[*] Format and mount the partition where your want to move your home directory somewhere (/mnt is usually a reasonable mount point):
```
mkfs.ext3 -L myhome -O dir_index /dev/mypartition
mont -t ext3 /dev/mypartition /mnt
```
[*] Mirror the files using the right tool for the job:
```
rsync -aS /home/. /mnt/.
```
Rsync is such right tool. Never use ```
cp -a
``` no matter what people tell you, ***it is not safe nor a filesystem mirror tool***.
[*] Delete the data from /home if you so wish, your decision. You probably want to if you are running out of disk space for other uses.
[*] Create an entry in /etc/fstab:
```
/dev/mypartion  /home ext3  defaults  0 2
```
[*] Mount the new directory: ```
mount -a
```
[*] Type exit and let the boot up process finish.
[*] Login to your account. You'll be using the new location.
[/list]

---

### Post by Vulpus on 2005-10-01
[QUOTE=mal]Just remember that your home folder holds much more than documents - it holds your personal settings for most applications (in hidden folders).
Also remember to preserve permissions when copying - use the "-p" option with the cp command.
Mal[/QUOTE]

This gives me cause for concern!  Perhaps it would be safer just to manually save stuff to my data HD and leave home where it is?

Thanks to everyone for the info though I have found it very useful.

---

### Post by GTvulse on 2005-10-01
[quote=Vulpus]This gives me cause for concern! Perhaps it would be safer just to manually save stuff to my data HD and leave home where it is?[/quote]

That's exactly why I do it the way I do it, to minimize the risk of PEBKAC and transfer all the data without alterations. 15 years of using Unix and Linux ain't fer nu'tting.  :-)

---

### Post by Karlos on 2005-11-20
i have moved my /home to another hard drive using the rsync method explained above.
everything seems to have gone well but I can't work out how to delete the old location .. any ideas .. cheers??

---

### Post by aysiu on 2005-11-20
[QUOTE=Vulpus]On MS Windows you can easily change the location of 'My Documents' to another folder or drive.  In my case i have changed it to D:\DATA so that all my data (my docs, my pictures, my music etc) is saved on a seperate partition.[/quote] You can save your data wherever you want. I also put all of my pictures, documents, and music on D:\. I mount that FAT32 partition as /windows in Ubuntu.

> 
Can you do the same thing with the 'Home' folder in Ubuntu?  At the moment the Home folder is on the Linux partition on  HDA1 but I would like to move it to HDB1 (which is a FAT32 partition). /home is not the same as data. It contains the equivalent of C:\Documents and Settings\Vulpus\. 

For example, in Windows, your Firefox settings are probably in C:\Documents and Settings\Vulpus\Application Data\Firefox. In Ubuntu, your Firefox settings are in /home/vulpus/.mozilla.

By the way, I would highly advise against putting any Linux-specific data (like your /home partition) on a FAT32 partition. You wouldn't put C:\Documents and Settings on an Ext3 partition, would you?

My advice? Keep your /home where it is and just move your data on to D:\ and mount D:\ with these instructions: [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

