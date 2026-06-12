---
title: "Cannot mount FAT32 partition"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by mit on 2006-07-22
hi,

From within XP i created a FAT32 partion, but i am unable to mount to it from within Ubuntu. :o  Any ideas where to start?

Error below;

Thanks for looking :D

---

### Post by jimmygoon on 2006-07-22
> **mit said:**
> hi,

From within XP i created a FAT32 partion, but i am unable to mount to it from within Ubuntu. :o  Any ideas where to start?

Error below;

Thanks for looking :D

How are you attempting to mount it?

---

### Post by taurus on 2006-07-22
Okay, open a terminal (Applications -> Accessories -> Terminal) and type

```

sudo mkdir /media/share
sudo mount -t vfat /dev/hda5 /media/share
df -h

```
And if that works, then add this entry (at the bottom) of your /etc/fstab so it would be mounted automatically upon boot...

```

sudo gedit /etc/fstab <-- to edit /etc/fstab

(Now, add the following line to it...)

/dev/hda5     /media/share     vfat     defaults,umask=0000     0  0

```

---

### Post by mit on 2006-07-22
Hi,

Thanks for your reply.  The first piece of code seemed to do something, but when i added the second part it told me there was no such directory.

:-k 

Thanks

---

### Post by jimmygoon on 2006-07-22
> **mit said:**
> Hi,

Thanks for your reply.  The first piece of code seemed to do something, but when i added the second part it told me there was no such directory.

:-k 

Thanks
(credit to taurus, just making it more n00b friendly, no offense intended)

type this in a terminal: ```
sudo gedit /etc/fstab
``` then add this line to the end of it: ```
/dev/hda5     /media/share     vfat     defaults,umask=0000     0  0
```

save, close and reboot

---

### Post by taurus on 2006-07-22
Let's take one step at a time.  So, you can see /dev/hda5 with the "sudo mount -t vfat /dev/hda5 /media/share" right?

Now, what did you type into the terminal for the second step?

```

sudo gedit /etc/fstab
(or you can go with a plain text editor like nano)
sudo nano /etc/fstab

```

---

