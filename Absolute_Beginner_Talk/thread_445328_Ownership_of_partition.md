---
title: "Ownership of partition"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by silkstone on 2007-05-15
If I plug in an external USB drive - formatted FAT32 - and look at Properties > Permissions, I am the owner and can do what I want.

But... I have a FAT32 partition on the internal HD which says it is owned by root. That isn't a problem because I can access it to read and write, but whenever I copy files to it the 'last modified' date is changed to the current time and date because (I think) it is changing the permissions. Also, I cannot create a link, even if I access by gksudo gedit.

Could someone please explain how to use the chown command, or edit fstab,  to change the ownership of this FAT32 partition?

The partition is named Data. It is mounted on /media/windows and is device /dev/hda5.

Many thanks in anticipation.

---

### Post by n8bounds on 2007-05-15
sudo chown silkstone:silkstone /media/windows -R

then

sudo chmod 777 /media/windows

simlinks don't work in FATland

good luck bud!

---

### Post by bodhi.zazen on 2007-05-15
naw, that will not work n8bounds :(

for fat you need to set ownership at the time of mounting or in fstab.

So start with: ```
sudo umount /media/windows
```

Now you have three options. The easiest is to edit fstab :

```
gksudo gedit /etc/fstab
```

And change the line to something like this :

> /dev/hda5 /media/windows vfat users,auto,uid=user_name,gid=users,umask=007  0 0

Then mount with ```
mount /media/windows
```


======


Or do not edit fstab and simply remount like this :

```
sudo mount /dev/hda5 /media/windows -o uid=user_name,gid=users,umask=007
```


======

Or you can use pmount, but you would have to edit a config file first ...

---

### Post by silkstone on 2007-05-16
Many thanks bodhi.zazen. Editing fstab as you suggest has sorted it. :)

---

### Post by n8bounds on 2007-05-17
Hey thanks for the correction.  I'll try not to shoot from the hip again like that.  (Would that have worked on a nice happy ext3 partition tho, or am I completely wrong?)

---

### Post by bodhi.zazen on 2007-05-19
> **n8bounds said:**
> Hey thanks for the correction.  I'll try not to shoot from the hip again like that.  (Would that have worked on a nice happy ext3 partition tho, or am I completely wrong?)

LOL, no problem.

Yea, what you suggested would work for any linux native partition. Mount the partition first, then chown/chmod the mount point.

---

