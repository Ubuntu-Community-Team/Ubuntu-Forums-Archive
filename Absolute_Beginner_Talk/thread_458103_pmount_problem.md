---
title: "pmount problem"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-29
Greetings,
Upon inserting my USB Flash drive into the front of my computer, into the USB port, it does nothing, and the icon appears in the notification area. I click on it, and "Open" is not lit. I click "Mount", and it displays this error:

> Unable to mount the selected volume.
error: could not execute pmount

I have been able to get my USB flash drive to work before, as I have used it on numerous occasions. I even tried the USB in another Ubuntu System, and it works. There must be something wrong with pmount.

Any ideas or suggestions of how to fix this problem would be appreciated!

Dr Small

---

### Post by Dr Small on 2007-05-29
Bump

I really need help with this!
Anyone that could help, I would appreciate just some tips!

Thanks
Dr Small

---

### Post by Inxsible on 2007-05-29
try:
```

sudo pmount /dev/sd* MyUSB

```

This should mount it under /media/MyUSB

post your fdisk -l and mebbe i could look into it more

---

### Post by Dr Small on 2007-05-29
I ran the command and it just outputed the usage of the command.
It wouldn't run it.

Dr Small

---

### Post by Inxsible on 2007-05-29
did you replace the * with the actual device name ?

can you please post the output of 
```
fdisk -l 
``` Thats a lowercase L

Make sure yourr USB is connected when you do this

---

### Post by Dr Small on 2007-05-29
I ran the command:
```
sudo pmount /dev/sdf1 MyUSB
```

It mounted it, but I can't access it, and then I ran:
```
fdisk -l
```

And it displays nothing.
Example:
> 
drsmall@drsmall:~$ fdisk -l
drsmall@drsmall:~$

Dr Small

---

### Post by Inxsible on 2007-05-29
I am sorry. Could you do a 
```
 sudo fdisk -l
```
 
and post the output

---

### Post by Inxsible on 2007-05-29
When you say it mounted successfully but you can't access it, what do you mean ?
 
Does it say that you dont have the necessary permissions ? If so, we might have to change the permissions on that drive

---

### Post by Dr Small on 2007-05-29
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15384   123571948+   7  HPFS/NTFS
/dev/sda2           29314       30401     8739360    c  W95 FAT32 (LBA)
/dev/sda3           15385       28959   109041187+  83  Linux
/dev/sda4           28960       29313     2843505    5  Extended
/dev/sda5           28960       29313     2843473+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 2142 MB, 2142240768 bytes
255 heads, 63 sectors/track, 260 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         261     2092000+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(259, 254, 63) logical=(260, 113, 45)



I am sorry for not clarrifing.
Yes, it says I don't have permission, so I logged nautilus in as root, went to /media/MyUSB and I had permission. So, it is a permission problem.


Dr Small

---

### Post by Inxsible on 2007-05-29
Ok in that case, you can change ownership like so 
```
sudo chown -R <your username> <your directory>
```
for you it would be 
```
sudo chown -R drsmall /media/MyUSB
```

---

### Post by Dr Small on 2007-05-29
Yes, but the problem still remains that it is not mounting when I first insert the USB.
I don't want to have to mount it via the command line, and make myself owner of the folder everytime I want to view or add files to my USB.

Dr Small

---

### Post by Inxsible on 2007-05-29
I think pmount needs to be performed only once. and it will always mount that drive in the same location always. The permission thing is also a one time effort. It does for me !!!

---

### Post by Dr Small on 2007-05-29
Well, the command  **sudo chown -R drsmall /media/MyUSB** doesn't seem to have an effect on the ownership of that folder, yet it doesn't output any errors.

I still can't access it under my account, without root access, (after I have mounted it and preformed the chown command) and when I remove it, reinsert it, I have to remount it again.

Dr Small

---

### Post by Inxsible on 2007-05-29
> **Dr Small said:**
> Well, the command **sudo chown -R drsmall /media/MyUSB** doesn't seem to have an effect on the ownership of that folder, yet it doesn't output any errors.
 
I still can't access it under my account, without root access, (after I have mounted it and preformed the chown command) and when I remove it, reinsert it, I have to remount it again.
 
Dr Small
 
Sorry man !!
 
pmount has always worked for me !!
 
Can someone else help us out here?
 
The other thing that you can do is this:
```

sudo mount -t vfat /dev/sdf1 /media/MyUSB -o iocharset=utf8,umask=000

```
 
Do this only if you are sure that your usb stick is FAT32 format -- mostly they are unless you formatted it differently -- mebbe to NTFS or something else

---

