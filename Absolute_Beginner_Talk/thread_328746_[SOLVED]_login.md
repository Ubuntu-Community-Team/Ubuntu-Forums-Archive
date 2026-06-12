---
title: "[SOLVED] login"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-31
I find that I no longer have to log in with UID or PW. Edgy boots into the desktop. I have tried several times to make sure it isn't my imagination. How do I check to find out if maybe I am root.

---

### Post by konst88 on 2006-12-31
```
whoami 
```

---

### Post by squrl on 2006-12-31
Thanks konst88. I am not logged in as root but now when I turn on the machine it never askes for UID or PW.  Kind of nice as long as it isn't the beginning of a nightmare.

---

### Post by taurus on 2006-12-31
Maybe you have the autologin enable...

---

### Post by squrl on 2006-12-31
Hi Taurus.  

Some of this stuff doesn't seem to show up till the next day. A simple reboot doesn't seem to make it surface but grab your socks the next morning. Kind of like a warm and cold boot in the dos days. 

Spent the last hour looking for a backup program I know I installed and now cant find it. 

This OS should have been called AI not ubuntu. Maybe I can get a transplant. lol

---

### Post by taurus on 2006-12-31
Do you remember what backup program you installed?

---

### Post by squrl on 2006-12-31
Yeah I have tried several but the one I was looking for is simple backup and finally found it.  I like it except that I doubt if it is backing up enough to really rebuild the system with a fresh install then dump the backup on it. Also the backups are on the install partition so if it goes down the backups go also.  Haven't found a way to have it put them on the external usb drive.

Its hell to get old and not be able to keep up with these young people.  Better yet on a network drive.

---

### Post by taurus on 2006-12-31
Sounds to me like you are talking about making an image of your drive in case you need to restore it later...

Is this something you have in mind?

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by squrl on 2006-12-31
I think you just identified what I am after.  I guess I really dont want a backup I want an iso image so I can get back to the last stable point. 

Please enlighten me Taurus. 

Thanks

---

### Post by taurus on 2006-12-31
Check out the link above!  It shows you how to take a snapshot of your system.

---

### Post by squrl on 2006-12-31
I went through the maze and did everything but had to cancel because I couldn't figure out how to save the image to the usb drive. Tried it letting it save wherever and it ran out of space. Gonna have to do some studying on this puppy.  I do think this is what I want if I can work out the details.

Thanks Taurus.

---

### Post by taurus on 2006-12-31
Did you mount your USB harddrive first and do you have permission to write to it?  How large is it and what format it is in?  You can select where to save it from the "**Image file to create/use**".

---

### Post by squrl on 2006-12-31
I checked it out a couple times but the only option I get is what partition to back up.



squrl@squrl-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3197    25679871    c  W95 FAT32 (LBA)
/dev/sdb2            3198        9729    52468290    f  W95 Ext'd (LBA)
/dev/sdb5            3198        6540    26852616    b  W95 FAT32
/dev/sdb6            6541        9729    25615611    b  W95 FAT32

If I read this right I want to image /dev/sda1 and it should go to /dev/sdb1/imagefileone which should be a 25 gig fat 32 partition on a usb external drive. 

Corrections please :)

---

