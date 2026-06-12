---
title: "[SOLVED] Help ! Can't Write to Shared partition"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-01
I just installed Feisty and created /,  /home and /shared partitions on my drive. However i see all the partitions under File System. Don't the Linux partitions show up as different drives like in Windows?
 
I also cannot create any folders in the /shared partition (which is a primary partition) although I can create folders in the /home partition(which i created as a logical partition)
 
Help !!

---

### Post by phiphedog on 2007-05-01
It's a permissions thing. Post you /etc/fstab file here so we can see what partitions you are mounting and we'll take it from there.

---

### Post by Inxsible on 2007-05-01
and how do i do that ? What command in the terminal should i type?
 
sorry..I am total noob here :(

---

### Post by Inxsible on 2007-05-01
This is my /etc/fstab file
```
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=128b67f7-2abf-4a31-b779-d698c8e6341d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=37f9ead7-b894-45af-bd5c-8910bfc1a267 /home           ext3    defaults        0       2
# /dev/sda3
UUID=1a2214f0-04ab-4b45-b3f8-c61682e7260f /shared         ext3    defaults        0       2
# /dev/sda1
UUID=282A7DE2679FB89D /windows/sda1   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=7458DD9C58DD5D84 /windows/sda2   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=6e3fc994-ff1c-489d-a0a3-391cf3e6e457 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


```

---

### Post by phiphedog on 2007-05-01
Your /etc/fstab file looks fine. Perhaps the /shared folder you created.

type this command in a terminal

[COLOR="Red"]sudo chmod -R 775 /shared[/COLOR]

then test it.

---

### Post by Inxsible on 2007-05-01
it didnt work !! :(


btw what does 775 stand for in that command ?

---

### Post by phiphedog on 2007-05-01
the chmod changes the permissions and the 775 means 
read write execute for the owner
read write and execute for the owners group
read and execute for everyone else

I'll assume your username is Inxsible for the following commands

[COLOR="Red"]sudo chgrp -R Inxsible /share[/COLOR]
[COLOR="Red"]sudo chown -R Inxsible /share[/COLOR]

This command above changes the owner and group of the folder /share to Inxsible and you should have write permissions. You can check this by typing

[COLOR="Red"]ls -ali /[/COLOR]

and you should have a line something like this (this is from my terminal)
[COLOR="Blue"]2 drwxrwxr-x  17 ben1 ben1     4096 2007-04-29 18:16 share1[/COLOR]

---

### Post by teddybairs1 on 2007-05-01
No, the partitions don't have anything remotely like the naming conventions of windows partitions. It is however more logical once you understand how it works.

Your primary partition is / (root). Think of this a the root on a tree that everything else (including storage devices like hard drives, flash drives, etc) grows out of.

The naming conventions for partitions and drives under linux go something like:

Master:
Hard Drive A partition 1 = hda1
Hard Drive A partition 2 = hda2

Slave:
Hard Drive B partition 1 = hdb1
Hard Drive B partition 2 = hdb2

and so on. In Feisty it renames it to sda instead of hda for some reason, but other than that it should follow the same pattern. Your windows drive, according to fstab is sda1 and sda2, both of which are mounted as ntfs format. In Linux, at this stage of the game, ntfs is still read only. You can't write to it, bu you can copy files from it into your linux home directory /home/[username] (root directory - home - your personal user folder)

Windows still uses the old DOS naming conventions for it's storage devices A: B: C: and so on. Linux treats everything as a directory branching off of root (/) including your drive partitions. Technically, your primary linux partition is mounted as root (/). The best way to think of it is that root (/) is like C:\. It's not a perfect analogy, but it will serve for now. The rest of your storage partitions should be found under /media.

Neither /home nor /shared are partitions, they are directories just as much as "Program Files" or "Windows" is a directory under C:\. The reason why you can't create any folders under /shared is because you need root priveleges to do it. Assuming you are running the Gnome desktop, open up Terminal and type: 

gksu nautilus

This will launch a confirmation of your password and then open up your file browser in root user mode which should allow you to create directories in any folder you please. Use it cautiously, especially if you really don't understand the filesystem. Ubuntu locks you out of root priveleges by default to keep the average newbie from permanently damaging his/her system by not knowing what they're doing. It's also another line of defense against would be malware and hackers, among others. Go into root at your peril. 

Hope this helps.

---

