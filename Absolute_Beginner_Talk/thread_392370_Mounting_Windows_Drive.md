---
title: "Mounting Windows Drive"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-03-24
[SIZE="4"]I have had so much success today that I think I've suprised myself.


We have two computers at home, set up on a small network.
Our main one, in the loft has sort of been taken over by my wife,,,,,which explains why I built this new computer.

Today, I finally figured out how to access the other computer's drives through our network and also managed to use the printer attached to the loft computer.
Turboprint was the answer for my Canon MP780.......and it works.
The main thing that eludes me at the moment is how do I see the files on the Windows partition of this drive?

I did this in Terminal and got this.

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9585    76991481    7  HPFS/NTFS
/dev/sda2            9586       19106    76477432+  83  Linux
/dev/sda3           19107       19457     2819407+   5  Extended
/dev/sda5           19107       19457     2819376   82  Linux swap / Solaris

Now, what should I do next?

Phil[/SIZE]

---

### Post by ljpm on 2007-03-24
If I understand you question correctly, you want to see the files on the Windows partition of the drive that also has you Linux partitions. This should be automatic. When I install a dual boot on my system icons were placed on the desktop allowing me to access the windows drive. If they are not there then try using Nautilus (Places, on menu).

---

### Post by groeswenphil on 2007-03-24
[SIZE="3"]Thanks,

When I click on PLACES,
I see all of my drives.
I can get into them all, except for one marked 73Gb volume.
I guess that this is my Windows partition.
When I click on it, I get this.

error: device /dev/sda1 is not removable

error: could not execute pmount

I get the same message if I try to mount the volume.

Thanks,
Phil
[/SIZE]

---

### Post by devils_casper on 2007-03-24
check /etc/fstab file. is there any entry for /dev/sda1? if there isn't, create a mount_point (folder) and add an entry for /dev/sda1.
```

sudo mkdir /media/sda1
gksu  gedit /etc/fstab
```

add this line
```

/dev/sda1 /media/sda1  ntfs  defaults,umask=0 0 0
```
save file, execute 'mount -a' command and check /media/sda1 folder.

---

### Post by groeswenphil on 2007-03-24
When I got to the MOUNT part, I got this.

mount: only root can do that


Thanks,
Phil

---

### Post by buuntuu! on 2007-03-24
try mounting as superuser then ;)
```
sudo mount -a
```

---

### Post by devils_casper on 2007-03-24
OR reboot your machine.

---

### Post by groeswenphil on 2007-03-24
[COLOR="Red"][SIZE="7"]
BINGO !!!!!!!!!!!!!!!
Works Now.
Big Thanks

:guitar: :guitar: 

Hey........Now, in Terminal it isn't asking me for a password. Is that because I'm logged in as a root user?
Phil
[/SIZE][/COLOR]

---

### Post by devils_casper on 2007-03-24
glad to help you. :) if you are logged in as 'root', you wont get password prompt. we have set umask value to zero in /etc/fstab file and it enables default access to all users.

---

