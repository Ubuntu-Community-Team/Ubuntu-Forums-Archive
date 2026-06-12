---
title: "mounting ext3 drives"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-08-29
I have two secondary hard drives, both in ext3 format.

One is /dev/hdb1 and the other is /dev/sdb1

I can access these drives by way of
1.in a terminal window entering sudo mount /dev/hdb1 /media/media, and sudo mount /dev/sdb1 /media/storage
2.opening up /media in nautilus, right clicking and selecting [root-nautilus-here]

It took me a while to get that far – both these drives started off as ntfs with all my stuff on them, all that stuff is now on sdb1... something that took me two days, and I'm quite proud of... but I digress...

I have learned that /etc/fstab is the file that tells my computer how to mount my drives on startup, and I  can edit it by way of sudo gedit /etc/fstab

My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1	/media/storage	ext3	uid=sean	0	0
/dev/hdb1	/media/media	ext3	uid=sean	0	0

Obviously, this ain't right... What should it look like so that it mounts on startup and gives me access without having to use root privlidges?

Peace,

Epi

---

### Post by taurus on 2006-08-29
You can mount them as normal and set the permissions to them...

```

/dev/sdb1 /media/storage ext3 defaults 0 0
/dev/hdb1 /media/media   ext3 defaults 0 0

```
Then from a terminal, do

```

sudo chmod 755 /media/storage /media/media
sudo chown sean:sean /media/storage /media/media

```

---

### Post by Episteme on 2006-08-29
I've followed those instructions - changing fstab options to 'defaults' now mounts the drives on startup.

However, I still need to root-nautilus to access them, otherwise, the /media folder looks like this (see attached screenshot)

I'm guessing that I should also:

```
sudo chmod 755 /media
sudo chown sean:sean /media
```

Is that right?

---

### Post by Episteme on 2006-08-29
HA!  IT WORKED!!

rebooted, and after doing this:

```
sudo chmod 755 /media
sudo chown sean:sean /media
```

I now have two new icons magically appearing on my desktop - one for each drive!  This rocks!!

Thanks again!

Peace,

Epi

edit:

I discovered that most of the files within sub-folders were still restricted and owned by root... I learned that

1. adding the switch -R to chmod makes it apply to all files and folders within that folder eg. sudo chmod -R 755 /media

2. adding the switch -hR to chown makes it apply to all files and folders within that folder eg. sudo chown -hR sean:sean /media

hitting 'refresh' in nautilus lets me see those changes without rebooting.

Holy crap - I think I'm getting the hang of it!

---

