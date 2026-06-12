---
title: "Hard Drive Problems"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by T4tav on 2007-01-20
Ive got 2 hard drives on my pc and overall i have got 3-4 partitions. If i try and access the partition that has windows on it , i get a privalige error , and the same with my empty hard drive too :frown:

---

### Post by Ecthelion on 2007-01-20
> **T4tav said:**
> Ive got 2 hard drives on my pc and overall i have got 3-4 partitions. If i try and access the partition that has windows on it , i get a privalige error , and the same with my empty hard drive too :frown:

How do you try to access those partitions?
And what is the exact error message that you get?

---

### Post by T4tav on 2007-01-20
Places > Computer > 70.7GB Volume : hdb1

You do not have the permissions necessary to view the contents of "hdb1".

---

### Post by Ecthelion on 2007-01-20
> Places > Computer > 70.7GB Volume : hdb1

Who do you see as owner when you right-click on it > Properties > Permissions

---

### Post by T4tav on 2007-01-20
[[IMG]http://img138.imageshack.us/img138/4453/screenshot8hc.th.png[/IMG]](http://img138.imageshack.us/my.php?image=screenshot8hc.png)

---

### Post by confused57 on 2007-01-20
This may work for you:

[http://www.ubuntuforums.org/showthread.php?t=333689&page=2](http://www.ubuntuforums.org/showthread.php?t=333689&page=2)

---

### Post by T4tav on 2007-01-20
> **confused57 said:**
> This may work for you:

[http://www.ubuntuforums.org/showthread.php?t=333689&page=2](http://www.ubuntuforums.org/showthread.php?t=333689&page=2)

Sorry , That didnt help much , All the drives are enabled and mounted but the permisions are not right so i cant access them

---

### Post by Ecthelion on 2007-01-20
Is that harddisk also mounted to /media/hdb1 ?
If so, try this...

```
sudo chown *username* /media/hdb1
```

Obviously, change "username" in your username :) 

chown means "change owner" 

you'll have to give in your admin passwor for the command :-)

---

### Post by T4tav on 2007-01-20
No good , It says 
```
chown: Changing ownership of `/media/hdb1` : Read only file system
```

---

### Post by Ecthelion on 2007-01-20
> **T4tav said:**
> No good , It says 
```
chown: Changing ownership of `/media/hdb1` : Read only file system
```

You did use sudo, did you?
Hmm
Could you post your fstab file?

```
gedit /etc/fstab
```

---

### Post by T4tav on 2007-01-20
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hdb5       /media/hdb5     ntfs    defaults        0       0
/dev/hdb4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Ecthelion on 2007-01-20
Hmm what I would recommend:
Backup your fstab
```
sudo cp /etc/fstab /etc/fstab_back
```
Open your fstab with admin permissions:
```
sudo gedit /ect/fstab
```
Then change this line
> /dev/hdb1       /media/hdb1     ntfs    defaults        0       0
to this line
> /dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

Then unmount your disk
```
sudo umount /media/hdb1
```
And mount it again
```
sudo mount /media/hdb1
```

---

### Post by T4tav on 2007-01-20
Thx , It works , Now i need to do it with the rest of the drives :)

I can access my filesystem / Ubuntu but i ant modify anything in it and i cant unmount it becasue ubuntu is on it

---

### Post by Ecthelion on 2007-01-20
> I can access my filesystem / Ubuntu but i ant modify anything in it and i cant unmount it becasue ubuntu is on it


That is completely normal.
Only someone with root permissions is allowed to modify files in /
The only files a normal user should modify are the files in /home/*username*/
This is one of the reasons why viruses don't have a chance. Only a root can change the filesystem.

---

### Post by T4tav on 2007-01-20
Is it possible to login as the root user ?

---

### Post by Ecthelion on 2007-01-20
> **T4tav said:**
> Is it possible to login as the root user ?

The use of the sudo command gives you root permissions.
So if you want to copy / move files in / you can give nautilus root permissions
```
gksudo nautilus
```
Or if you want to edit a file
```
gksudo gedit */filepath*
```

If you enter your root password once it'll stay active till you are inactive for 15 minutes.
After that you'll have to enter it again.
The use of sudo is mainly for not graphical purposes. When you want to use sudo for something graphical (like nautilus etc), use gksudo instead

---

### Post by T4tav on 2007-01-20
Thx for all the help :biggrin:

---

