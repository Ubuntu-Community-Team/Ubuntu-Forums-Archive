---
title: "Permissions: Write to FAT32"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Aurdal on 2006-06-04
Ok, so I just figured out I don't have permissions to write to my FAT32 disk without being logged in as root.

I can't seem to change the owner of the mounted drive, and I can't chmod it to 777 as it wont go higher than 5 on group or on other users. Can anyone please tell me how to actually be able to write to this disk with my regular user?

---

### Post by stevanbt on 2006-06-04
Hi,
I have the following in my /etc/fstab:-

```
/dev/hdb1       /media/hdb1     vfat    umask=0000,dmask=0000,uid=0002,gid=users,users  0 0
```

It allows me (as I'm a member of the users group) to create and delete files and directories on the fat partition.  You should be able to add it to your /etc/fstab file then run ```
sudo mount -a
```

To be honest I don't know what all the settings do (I'm sure someone else will be able to tell you if they're all required or not) and I can't remember where I got it from.

Hope this helps, Steve.

---

### Post by uzi09 on 2006-06-04
try this:

sudo chown user:user /mnt/hda1

sub in your user name for user
sub in the location of the mount point for /mnt/hda1

ps: i think the above method is probably better :D

---

### Post by Aurdal on 2006-06-04
Thanks, that set it to 777. 

:)

---

