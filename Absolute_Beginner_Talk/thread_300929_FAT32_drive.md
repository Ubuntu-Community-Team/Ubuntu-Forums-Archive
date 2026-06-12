---
title: "FAT32 drive"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by claretsfan on 2006-11-16
Just installed Ubuntu, without a hitch.  However, I can't get write access to my FAT32 drive.  I can read it from Ubuntu, and it appears to be mounted correctly (maybe?), but I can't delete, save or alter documents on there.

The "properties" info tells me that all permissions are for "root".

I tried this:

[I] How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write

    * Read #General Notes
    * Read #How to list partition tables 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

    * Append the following line at the end of file 

/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0

    * Save the edited file [/I][/I]

But it doesn't seem to work.  My fstab looks like this:

/dev/hdb5    /media/windows vfat  iocharset=utf8,umask=000  0    0

I think that looks about right (the disk is hdb5, from what I can remember when I partitioned)  /media/windows is where I can see the drive.

Any ideas?

Thanks in advance

---

### Post by Bachstelze on 2006-11-16
try to add the option *uid=xxxx*

where xxxx is your UID, you can get it with :

```
cat /etc/passwd | grep your_login_here
```

(You can specify a GID as well)

---

### Post by claretsfan on 2006-11-16
That was quick- thanks!

It's telling me that the xxxx is 1000.  Does that seem likely?  Whereabouts in the fstab line do I enter uid=1000, assuming that's correct?

---

### Post by Bachstelze on 2006-11-16
```
/dev/hdb5 /media/windows vfat iocharset=utf8,uid=1000,umask=022 0 0
```

should be OK, at least it works for me.

---

### Post by claretsfan on 2006-11-16
Brilliant- sorted!

Thanks for the help

---

