---
title: "How to view use fat32 partition with Ubuntu"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Fibre on 2005-12-30
I want to wipe my ubuntu O/S off and start again but I first want to save alot of work onto the fat32 partition I made before installing Ubuntu the first time.

I've got some problems that aren't resolved and it would take me less time starting from scratch then waiting for answers that don't come for hours if at all.

Please if somebody could just tell me how to access my partition (fat32) which I can't see for some reason in "places".

Do I have to mount it somehow?

---

### Post by thekiller on 2005-12-30
look into the output of

```

more /etc/fstab

```

and look out for [COLOR="Red"]vfat[/COLOR]

say /dev/hda1 is recognised as  [COLOR="Red"]vfat[/COLOR], then to mount it do

```

mount /dev/hda1

```

Now suppose you want to copy the folder /home/ubuntu/music under your fat32 partition, then just do

```

cp -R /home/ubuntu/music /dev/hda1

```

---

### Post by Fibre on 2005-12-30
This is what I got so I don't know?

On my hard drive I've got xp/ 6gb of fat32/ Ubuntu- in xp the fat32 drive is recignised. but after doing [COLOR="Red"]more /etc/fstab[/COLOR]all I get is this:-

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I think I'll have to just start from scratch, thanks for the reply thekiller. 

I'll just start from scratch and practice everything that I've already learned all over again. It's a pain but at least that way I will become quite good at this.

I'll just copy what I really need to a 700mb disc and go from there thanks mate.

---

### Post by Suger on 2005-12-30
Well, don't do that yet, we might find it.

What's the output of ls /dev/hda* ?

---

### Post by Fibre on 2005-12-30
It's done but I still would like to find the partition anyway.

All is the same but Ubuntu is just been re-installed a new.
fibre@ubuntu:~$ more/etc/fstab
bash: more/etc/fstab: No such file or directory
fibre@ubuntu:~$ ./etc/fstab
bash: ./etc/fstab: No such file or directory
fibre@ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
fibre@ubuntu:~$ is /dev/hda*
bash: is: command not found
fibre@ubuntu:~$ ls /dev/hda*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda3  /dev/hda5  /dev/hda6
fibre@ubuntu:~$

I hope this is what you wanted to know - _second last line_

I still have xp / 6gb or fat32 and Ubuntu. It's just a new install to save on a search that had taken twice as long as it took me to re-install and update.

Also side question I've installed firestarter when I tried open it in Terminal I get :-
a window that says I have insufficient privileges - You must have root user privileges to use firestarter?

---

### Post by Suger on 2005-12-30
try 
```

mount -t vfat -o iocharset=utf8,umask=000 /dev/hda1 /mnt

```
if it works, ls /mnt should show you the content of your fat32 partition. If it fails, try the same command, substituting /dev/hda5 or, should that fail, /dev/hda2. One of them is your fat32 partition. Once we know which one, modifying the fstab to have mount at startup will be a breeze.

---

### Post by aysiu on 2005-12-30
See the fourth link of my sig.

---

### Post by Suger on 2005-12-30
](*,) I had not thought of fdisk -l.

---

