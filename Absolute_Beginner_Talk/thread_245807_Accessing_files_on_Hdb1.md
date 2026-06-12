---
title: "Accessing files on Hdb1"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by tobmeister on 2006-08-28
HOw do I access the files on my secondary harddrive?  I have saved all my giles from my previous OS (xp) and other files as well.  I would like to be able to get to them

Thanks

Tobmeister

---

### Post by Metacarpal on 2006-08-28
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by sonny on 2006-08-28
First you have to know what type of FS you HD has... is it NTFS, FAT31, FAT16, EXT3???

To access your HD you have to mount it first, if it doesn't mount at boot. To mount your hard drive you have to do the following in a terminal:

sudo mount = this is the mount options, only root can mount therefore the sudo.

-ntfs = then you have to specify what FS is the HD, ntfs or fat

/dev/hdb1 = the location of your HD, all drives are in /dev (devices)

/mnt/hdb1 = the location where it's going to be mounted. You can change this for anywhere you like (you'll have to make a folder with that name), /home/$user/Documents to mount it in your home.

The full command would be:
    sudo mount -ntfs /dev/hdb1 /mnt/hdb1

---

### Post by nrwilk on 2006-08-28
If you installed ubuntu with the disk in the system, an entry for it should have been automatically created in your /etc/fstab file.

If this is the case, the disk should be mounted at /media.

first try this in a terminal:```
ls /media
``` 
This will just list the files and directories in the /media directory.

You should get output that looks like this:```
user@computer:~$ ls /media
cdrom  cdrom0  sda1  sda3
``` 

from this output, we see that I have two partitions mounted in /media.  They are sda1 and sda3.

to see the contents of these partitions, just access them through their mountpoints (/media/sda1).  Again, use the "ls" command to list the contents of directories.

So, assuming that you find a partition called hda2 in your /media directory, issue this command:```
ls /media/hda2
``` 
when I do that I get this output:```
user@computer:~$ ls /media/sda1
boot.ini                hpqp.ini      pagefile.sys   System Volume Information
Config.Msi              I386          Program Files  vongo
Documents and Settings  MWInstall     RECYCLER       WINDOWS
hiberfil.sys            ntdetect.com  SWSETUP        XP_TV.ini
hp                      ntldr         system.sav

``` 

I see that this partition has directories called "Documents and Settings" and "WINDOWS."  Form this output I can tell that I've just accessed the very top level of my Windows partition.

now that you know where you want to go, go to your file browser and type /media/hda1 into the path bar (or whatever partition it is that you found to contain Windows).  From there, you can browse your windows files with ease.

---

### Post by tobmeister on 2006-09-02
Hey Metacarpal,

That site ([http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)) was a life saver.  I tried the 

sudo mount -fat /dev/hdb /mnt/hdb

But had no success so I went into the apt and added the line for the hdb and saved it and sure enough it worked no problem.

Thank you all for the help in this one of many issues I'm sure to have as a newbie

Tobmeister

---

### Post by nrwilk on 2006-09-02
I'm glad you figured it out! :D

nrwilk

---

### Post by Seryozha on 2006-09-02
i tryed sudo mount -ntfs /dev/hda5 /home/seryozha/Desktop
 and i get:
mount: unknown filesystem type 'fs'


any help?

---

### Post by Seryozha on 2006-09-02
> **Seryozha said:**
> i tryed sudo mount -ntfs /dev/hda5 /home/seryozha/Desktop
 and i get:
mount: unknown filesystem type 'fs'


any help?

i got this working from help on the psycocats site. thanks

---

