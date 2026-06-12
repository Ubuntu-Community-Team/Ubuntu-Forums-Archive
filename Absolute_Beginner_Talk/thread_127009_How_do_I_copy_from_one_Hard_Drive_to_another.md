---
title: "How do I copy from one Hard Drive to another"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by the_beer_chef on 2006-02-07
I just mounted my second hard drive /dev/hdb1 on to Ubuntu.  It is an EXT3 format for Ubuntu only.  I don't know why I cannot copy files between my prmary drive  and this new drive.  My primary drive says the owner is "ralph123" (my example login) and the other drive says the owner is "root". 

How can I copy and paste files between the to for multi-media, misc file etc.... I guess I am thinking like windows and moving stuff from C: to D:

How do I do this in Ubuntu?

:confused:

---

### Post by funkydan2 on 2006-02-07
Post your /etc/fstab file here so that we can check that the line for hdb1 is correct.

---

### Post by the_beer_chef on 2006-02-07
**Here's my fstab:**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/emil_d   ext3     defaults

Any Clue to why I cannot copy from one harddrive to another?

---

### Post by funkydan2 on 2006-02-08
yep - what are the permissions/ownership of the mount point?
'ls -l /media/emil_d' will tell you that.  Odds are the beginning of the output will look something like this

drwxr--r--

which means that only the owner of the directory can write to it (e.g. the root user).  You'll need to change the permission/ownership on that directory so that your normal user can access it.

'sudo chmod 777 /media/emil_d'

should do the trick.

---

### Post by Sutekh on 2006-02-08
[QUOTE=funkydan2]yep - what are the permissions/ownership of the mount point?
'ls -l /media/emil_d' will tell you that.  Odds are the beginning of the output will look something like this

drwxr--r--

which means that only the owner of the directory can write to it (e.g. the root user).  You'll need to change the permission/ownership on that directory so that your normal user can access it.

'sudo chmod 777 /media/emil_d'

should do the trick.[/QUOTE]

**chmod** will change the permissions, but not the ownership.  If the folder has sub-directories it might also be useful to use the **-R** flag to make the chmod command recursive thorugh all children folders
```
sudo chmod **-R** 777 /media/emil_d
```

funkydan2 is right, if you change this you should have read/write/execute permissions (the **rwx** in his example) to the folder /media/emil_d

If you wish to take **ownership** of this folder (depending on whats on the partition this may not be a good idea, if its just data then ok, if its an important Ubuntu filesystem perhaps not)
```
sudo **chown** -R ralph123 /media/emil_d
```
will change the ownership of the folder /media/emil_d to ralph123, your example login.

---

### Post by the_beer_chef on 2006-02-08
Tried that this morning and it seemed to work. 

Thank You...

---

