---
title: "Accessing Old Hard Drive thru' Ubuntu"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by zmike on 2006-12-28
Hi,

I accidentally burnt down my mobo the other day but I need to recover some files from the hard drive so I will be going over to a friends house to do so. I've tried getting the files but using windows but the I get the "incorrect parameters" message. So now I was thinking of using Ubuntu. I have a live CD for ubuntu but I don't know how to access my files in a NTFS hard drive (last time, it asked me to mount the drive???).

**Short Question: How could I recover my files from a NTFS hard drive using a Ubuntu live CD?**

thanks

---

### Post by taurus on 2006-12-28
You need to mount your harddrive from a terminal under LiveCD and recover your files...

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows -o umask=0222
(assuming it's on /dev/hda1 and ntfs filesystem...)
ls -la /mnt/windows
```

---

### Post by K.Mandla on 2006-12-28
It shouldn't be too tough. Basically, you want to attach the drive to a computer, boot the live CD, then

```
sudo fdisk -l
```
to find the assignment for the drive. It will probably look something like /dev/hdb1.

Next make a partition to mount the drive to:

```
sudo mkdir /media/windows
```
Now mount the drive with:

```
sudo mount /dev/hdb1 /media/windows -t ntfs -o nls=utf8,fmask=0333,dmask=0222
```
Now you should be able to read the files on the drive by looking inside /media/windows. 

Give it a try and see what happens.

Edit: Darn! taurus beat me by seconds!

---

### Post by taurus on 2006-12-28
> **K.Mandla said:**
> 
Edit: Darn! taurus beat me by seconds!

](*,)

---

### Post by zmike on 2006-12-29
I just have 3 questions before I begin. 

Should I set the hard drive to master or slave?
Can I copy all the files to a 4 gb usb drive once the drive is mounted?
Is there anything that I need to be very careful about to avoid data loss?

thanks

---

### Post by taurus on 2006-12-29
1.  Doesn't matter.  But if it is the only harddrive on your machine, might as well set it to master, /dev/hda...

2.  What format is that USB drive?

3.  Just copy your data over and you're done.

---

