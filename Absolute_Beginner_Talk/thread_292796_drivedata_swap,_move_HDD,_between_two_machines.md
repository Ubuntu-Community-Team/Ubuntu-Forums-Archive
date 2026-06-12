---
title: "drive/data swap, move HDD, between two machines?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by nicknormal on 2006-11-04
I have two machines, both running 6.06.

Older machine has 160Gigs HDD; newer machine has 300Gigs. I want to get the data from the older machine to the newer machine. I'm not interested in file structure, user settings, etc.; only interested in raw data, things like PDFs, MPGs, AVIs, etc. Is it possible to put the older drive into the newer machine and somehow recognize the drive, even though it used to run Ubuntu, or will the newer machine not allow it?

Really naive question i know. Obviously for security reasons it would make sense to not recognize the drive, so I'm curious what's the easiest way to get that data to the newer machine? Crossover network cable? Or is there something I can do to mount the older drive to *see* the data and copy it over to the newer drive, from inside the same machine?

thanks!

---

### Post by podunk on 2006-11-04
You would just need to jumper the drive properly, install it in the drive chain of the new machine and then mount it in fstab. 
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by nicknormal on 2006-11-04
podunk,

howdy!

so i followed your instructions and after i typed:

sudo mount -a

i received the following:

wrong fs type, bad option, bad superblock on /dev/hdb1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

beyond that, i don't know what to do.

knowing that you might ask me what my drive map looks like, when i type
sudo fdisk -l
i get:

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19364   155541298+  83  Linux
/dev/hdb2           19365       19457      747022+   5  Extended
/dev/hdb5           19365       19457      746991   82  Linux swap / Solaris

the /dev/hdb1, the boot sector, is the space i'm interested in, which contains the original data. is there still a way to access this data???

cheers!
Nick Normal

---

### Post by podunk on 2006-11-05
Hey nick,

This is what i would try (and hopefully if it's wrong someone will jump in and correct me.) I doubt you can hurt anything doing this. You *are* using dapper - right? the file system syntax is different for edgy as far as i can tell.

Open a terminal and create a mount point;
```
sudo mkdir /mnt/music
``` instead of "music" you can use anything you want, just_leave_no_spaces_in the name

I would open and edit my fstab file as root:
```
gksu gedit /etc/fstab
``` note that you will see an error in the terminal when you hit enter – ignore it.

I would insert the following line:
```
/dev/hdb1	/mnt/music	ext3    defaults,errors=remount-ro 0       1
``` note that the spaces in the command are really tabs

Save the file and <blush!> restart the computer. When you come back up you should be able to browse it with nautilus.

---

