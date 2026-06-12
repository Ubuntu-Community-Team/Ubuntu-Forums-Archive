---
title: "trying to get drives mounted."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-04-20
I went to wiki and tried all 3 of the methods they said to do.None of them worked as far as getting my hard drives mounted.C mounts from start-up and D and E doesn't for some reason.I can't even find them on my system.I went to the command line and I can see them there and that is the only place,can somebody please help.

---

### Post by amaroKer on 2007-05-04
open gparted and see what the partition names are.  Mine are **/dev/sda1 /dev/sda2** etc.  Mount those devices under a folder that you make with **mkdir** using the **mount** command

---

### Post by Inxsible on 2007-05-04
First you need to run this command: 
```

fdisk-l 

```
Note that l is small L and not 1

Note the drives name. It should be something like /dev/sda2 or /dev/sdb1 etc.

Then you need to edit your /etc/fstab
```

sudo gedit /etc/fstab

```

and add the following to it
```

<drive-name>  <MOUNT_POINT> <the-file-system-of-the-drive> defaults,errors=remount-ro 0 1

```

Your MOUNT_POINT is any location where you want the drive to be for eg. /media/MyDrive
File system could be ntfs-3g or ext3 or whatever your filesystem is
Then create a mount point for the drive 
```

sudo mkdir <MOUNT_POINT>
sudo mount -text2  <drive-name> <MOUNT_POINT>

```

and you should be done :)

---

