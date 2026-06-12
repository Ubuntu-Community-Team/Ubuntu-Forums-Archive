---
title: "Installed second hard drive cant use partitions"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by zFb on 2008-02-16
I just formated my second hard drive for Ubuntu "7.10" I have them formated to ext3. I cant do anything in the new partitions anytime I try it says I don't have permission.

---

### Post by wolfen69 on 2008-02-16
are you trying to install to the new drive? or is it for storage?

---

### Post by MasterJS on 2008-02-16
The partitions cannot be mounted, if they are mounted you need to unmount them.

---

### Post by zFb on 2008-02-16
For storage , sorry.

---

### Post by MasterJS on 2008-02-16
do you have the drive mounted when trying to use them?

---

### Post by zFb on 2008-02-16
Well, I used gparted and unmounted them. Nothing seemed to change.I have no idea how Ubuntu file systems work  when I try and open a partition it mounts.

---

### Post by paulstaf on 2008-02-16
Edit your /etc/fstab 

sudo gedit /etc/fstab

and then add a line to the bottom:
 
/dev/YOURDRIVE       /MOUNTPOINT    ext3 user,auto 0 0 

put your device and mountpoint in there.

Then unmount the drive if it is mounted and remount it by typing:  

sudo mount -a

And it should remount where you want.

You may have to change the user and group to your name for the mountpoint

So let's say your mountpoint is:  /media/usbdrive  you can do:

 sudo chown myuser:myuser /media/usbdrive

This will make YOU the owner of that folder and should give you read and write permissions to it.  If not, then do:

sudo chmod 777 /media/usbdrive

Hope this is what you were after.

---

### Post by MasterJS on 2008-02-16
What exactly are you trying to do on this second hard drive? You said you needed it for storage. If you can't use the partitions, that means it wasn't formatted correctly. I would recommend using the Live CD, typing gparted in a terminal, and using it from there.

---

### Post by zFb on 2008-02-16
So, I got about 2 steps into that before I got stumped. I opened the text file. I added the line to the bottom.And changed YOURDRIVE to sdb1. I don't know what a mountpoint is. I googled it and found nothing explaining it. If I knew what that is I'm sure I can figure the rest out.

---

### Post by wolfen69 on 2008-02-16
your mount point would be /media/sdb1

---

### Post by wolfen69 on 2008-02-16
when working within the live cd, i first do
```
sudo su
```
which will make you root.

then do
```
umount /dev/sdb1
```
if sdb1 is the drive you want. that will make sure it is unmounted.

then
```
gparted
```
you will now be able to make changes to your drive. hit apply. sometimes gparted will crash after an operation. just type gparted again to restart it. hope this helps.

---

### Post by zFb on 2008-02-16
Figured it out thanks for the help guys.

---

### Post by zFb on 2008-02-16
OK , I guess i didn't do it right. So I started over. After i edit the fstab and enter the new line with my drive (sdb1) and mount point(media/disk). Then i enter code.
> sudo mount -a
which returns
> mount: mount point /media/disk does not exist

---

### Post by wolfen69 on 2008-02-16
you first need to do
```
sudo mkdir /media/disk
```

you can of course replace "disk" with anything you want

---

### Post by zFb on 2008-02-17
that did it thanks guys

---

