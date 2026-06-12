---
title: "Automounting part x"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by someusernoob on 2006-06-08
Well, i thought, since i do not officially want to use Windows anymore, i can make my 2nd HDD EXT3, so i could easily read/write data to it. Since FAT32 only supports up to 32GB and the HDD is 120GB it was an easy choice + i thought it would be SO SIMPLE to just have an extra EXT3 drive.

BUT

I can not figure out how to automount it and have full access myself, as a user. I got it to automount once, but only the root could write to it, and hey, thats what i tried to avoid, only reading from a disk.

When you use the search everyone is worried about automounting FAT32 and NTFS disks. 

Ive been surfing for over an hour now, searching and reading but cant get it done. ](*,) 

Ths is my fstab file now:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

The EXT3 HDD i'd like to mount is /dev/hdb5 and i'd like to mount it on /media/Data. And i want full access to it myself, as user. Can someone help me with this one?

And why is it so hard to just setup a Linux partition under Linux?

Ps: i tried /dev/hdb5 /media/Data ext3 defaults 0 0, but thats the one which i can only read, and only the root can write.

---

### Post by someusernoob on 2006-06-08
For all those out there having the same trouble:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

This is clear and a piece of cake. And as always; you just have to know.

It's now up and running, finally :P

---

