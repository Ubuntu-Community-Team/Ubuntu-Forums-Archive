---
title: "[SOLVED] format external usb"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-24
every time i format a hard drive with gparted to ext3 it comes up with a lost and found folder and is not available.

it happens whether it is an external usb drive or an internal slave

this one is an external drive in a usb box.

how can i get it to be available is it about permissions or what???????

help i am very frustrated

what do i need to do differently????

thanks
db

---

### Post by newlinux on 2007-08-24
When you say it is not available what do you mean? Do you mean  you can see it but not write to it? If so, it probably is about permissions. The lost and found folder is where is created by the ext3 filesystem.

Where is the drive mounted?

can you post the output of
```

ls -l *path-to-drive*

```

where path-to-drive is where the drive is mounted, like /media/usbdisk or something.

---

### Post by DarinB on 2007-08-24
this is what i got i have no idea what it means

darin@darin-desktop:~$ ls -l /media/disk-1 
total 16
drwx------ 2 root root 16384 2007-08-24 11:21 lost+found

---

### Post by DarinB on 2007-08-24
i deleted the lost and found directory on the external drive but it won't read write says no permission

---

### Post by schorsch on 2007-08-24
Well, the "lost+found" folder belongs to the ext3 filesystem and is created automatically when creating the filesystem. When there were some errors during filesystem checks some fragments go there. But this directory is not available to "normal" users.
It is not critical that you removed it as it will be created again during the next filesystem check. BTW: reiserfs has no "lost++ound" folder as it works in a totally differen way.
But back to you problem: Please post the output of
```
ls -ld /media/disk-1
whoami
id
```

---

### Post by newlinux on 2007-08-24
> **DarinB said:**
> this is what i got i have no idea what it means

darin@darin-desktop:~$ ls -l /media/disk-1 
total 16
drwx------ 2 root root 16384 2007-08-24 11:21 lost+found

That indicates only root has the ability to read and write (and execute) to this disk. Try:
```

sudo chmod a+rw /media/disk-1
```

which should add read and write permissions for all users.

---

### Post by DarinB on 2007-08-24
well here is what i tried tell me what you think.
i went into terminal and went in as root
chown usr:usr /media/disk-1
for usr:usr i use my name darin:darin
it instantly mounted and was accessible.
i removed it rebooted and it came up as /media/disk instead as disk-1 bu tit is still accessible.
whadya think??

---

### Post by DarinB on 2007-08-24
would it be better to try the 

sudo chmod a+rw /media/disk-1

in the future???

---

### Post by newlinux on 2007-08-24
It depends on what you want. If all you want is for the user darin to have access to it, then the first way is fine (it means the user darin owns the directory and it is in the group darin). The way I sent would allow all users the ability to read and write to the drive, but the drive would still be owned by root (so only root could change permissions on the drive).

The way you have done it is fine, and the user darin can now change permissions on the drive to allow others to use as well.

---

### Post by newlinux on 2007-08-24
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

Might be helpful for background...

---

### Post by DarinB on 2007-08-24
great tutorial on permissions thanks everybody you guys are the best.

one question why does this happen when i create a new est 3 partition with gparted whether on an internal or external drive.

i now know that it doesn't with ntfs or fat since those don't' accept permissions but they also don't mount at boot up (another issue)

what do the experts say? can i make a new partition differently to avoid the issue.

thanks db
love ubuntu more and more everyday
wish i would have done this earlier

---

### Post by schorsch on 2007-08-24
Because gparted is run as root and so every device created this way belongs to root. Just remember to change the owner as desired after creating a new device.
Sorry, I do not know any other way .... but take a look on the other side: If in a multiuser system every one could create devices as he/she likes, what would be the result?

---

### Post by DarinB on 2007-08-24
thank you

---

### Post by newlinux on 2007-08-24
> **DarinB said:**
> great tutorial on permissions thanks everybody you guys are the best.

one question why does this happen when i create a new est 3 partition with gparted whether on an internal or external drive.

i now know that it doesn't with ntfs or fat since those don't' accept permissions but they also don't mount at boot up (another issue)

what do the experts say? can i make a new partition differently to avoid the issue.

thanks db
love ubuntu more and more everyday
wish i would have done this earlier

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Might help you with automounting windows partitions. Also, if you want to mount an external ext3 drive to the same place every boot there is a little more you will need to do with the drive label. Just ask if you are interested or search the forums.

---

