---
title: "harddrive permissions change from root"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by stylechild on 2008-04-19
hey i have sorted the issues out regarding the partitions.. 
but hit a 2nd problem..

i only have read access..
and the "owner" is unknown..

how can i change it so i have the read an write permissions?


:guitar:

---

### Post by benerivo on 2008-04-19
I think the answer lies in your /etc/fstab file. Can you post the contents of this here?

---

### Post by joshrobinson on 2008-04-19
```
cat /etc/fstab
```

also could you tell us what drive it is your having the problems with

---

### Post by stylechild on 2008-04-19
stylechild@stylechild-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e0830f0c-5f93-419a-88df-8b0978ac2eb6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=be7bc267-c4cb-4710-a664-e017fe08294a /usr            ext2    defaults        0       2
# /dev/sda2
UUID=61a018dc-9ba3-4360-a35d-5c3b227dbf08 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
stylechild@stylechild-laptop:~$ 


had a boot issue from messsing about so just reloaded and updating 

but thats the details from a new install

i wanna use UUID=be7bc267-c4cb-4710-a664-e017fe08294a /usr            ext2

thanks

---

### Post by stylechild on 2008-04-19
grr..

im guessin as i set mount as " /usr " is the reasons it wont allow me to unmoun/format or even see it with out the partition editor?

so, lets try it this way..

how do i now, change the mount point?

once changed, repartition an remount..

then make it so i can read an write to it using stylechild..


plus while i got u geniuses is it safe to ignore the "errors=remount-ro 0 1" ??

---

### Post by bumanie on 2008-04-19
Before trying to change anything backup your present fstab > sudo cp /etc/fstab /etc/fstab_backup I am not an expert, but as far as I know you can ignore errors=remount-ro 0 1. I think you are right with your suspicion about /usr As I said, backup first and make sure the backup file is there before continuing. I would try changing /usr to [COLOR="Red"]/media/sda3[/COLOR] and see if that works - it should, but if not you can change it back to how it is now or use your backup to get it back to how it is now.

---

### Post by benerivo on 2008-04-20
> **stylechild said:**
> how do i now, change the mount point?

once changed, repartition an remount..

then make it so i can read an write to it using stylechild..?

Changing the mount point won't make it writbale for you as it will still be /usr, which is only writable if you have root permissions. You can temporarily gain write permissions with nautilus if you run```
gksudo nautilus
```or you can set this partition so that it is permanantly writable. ***Be aware you can break the system if you change something in /usr that you shouldn't.***

You should be able to change the permissions of the current mount point by changing the line in fstab to read```
UUID=be7bc267-c4cb-4710-a664-e017fe08294a /usr ext2 user,auto,rw 0 2
```then run```
sudo chmod 777 /usr
```I think this would work, but always make a backup and have a live cd which you can use to restore the file if you try this and it fails to boot.

---

