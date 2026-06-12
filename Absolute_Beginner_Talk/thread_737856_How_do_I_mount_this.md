---
title: "How do I mount this?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by xl_cheese on 2008-03-28
It's late and I'm tired.  I've been searching for 2 hours on how to do this.

I just want to call it mospace and have it show up in the file browser and a 2nd harddrive.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0755

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux


Thanks.

---

### Post by virtuallinux on 2008-03-28
I may be able to help you, but you're right, it's late (1:30 for me).  I'll try and remember to take a look at this tomorrow evening, I may be able to help.

---

### Post by xl_cheese on 2008-03-28
I found this great lil site.  Figures I spent 2 hours then call for help.  10 minutes later I have my answer.  [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I created an ext3 partition on the entire drive.  I had already been looking at fstab, but did not know what to put in there.

I just had to add this:
```
/dev/sdb1   	/media/mospace  ext3    defaults   0   0
```

---

### Post by virtuallinux on 2008-03-28
Ok, good to hear you've got it working.

---

### Post by Jnetty99 on 2008-03-28
Would this work the same if I want to mount a USB hardware but formatted in NTFS format?

---

### Post by virtuallinux on 2008-03-28
Well, in theory, anything that is USB should auto mount, according to the name of the disk.  For instance, I have a flash drive called 2GBUSB.  When I plug it in, it mounts itself under /media/2GBUSB.  It does all the hard work automatically.

---

### Post by Jnetty99 on 2008-03-28
I checked the /media folder and that drive is not listed. 
By the way i'm running this on Ubuntu Server. 

I did the sudo fdisk -l and it was listed.

---

### Post by Inxsible on 2008-03-28
if you use the command ```
df -h
``` it will also show you where it is mounted.

---

### Post by Jnetty99 on 2008-03-28
```
df -h
```
gives me
```
 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  607M   35G   2% /
varrun                125M   40K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   60K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm 
```


I just did this before the suggestion above. 
```

jnetty@test:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00067051

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4905    39399381   83  Linux
/dev/sda2            4906        4998      747022+   5  Extended
/dev/sda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91559155

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS 
```

I decided to make a folder in /Home/Me/Storage
then open and edited the /etc/fstab and added
```
 /dev/sdb1    /home/me/storage   ntfs  defaults 0 0 
```

then ran ```
 sudo mount -a 
```
and got the following back

```
 $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /home/jerry/storage -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /home/jerry/storage ntfs-3g defaults,force 0 0
```

---

### Post by Inxsible on 2008-03-28
One, /Home/Me/Storage is different than /home/me/storage.

Two, connect the external to a windows machine and do the 'Safely remove hardware' thingy for that drive. and then login to ubuntu again and try.

---

### Post by akiratheoni on 2008-03-28
Also keep in mind that if you want to mount an NTFS partition or hard drive with Windows on it, Windows has to be completely shut down... in other words, Windows can't be suspended or hibernating.

---

### Post by Jnetty99 on 2008-03-29
I think I got it mounted now. 
I took the drive to a Windows system and reformatted and then clicked the 'safely remove device'.

restarted the Ubuntu Server and connected and did the changes to fstab and did mount -a and got no errors. 

How can i tell that its mounted properly to my /home/me/storage folder?

---

