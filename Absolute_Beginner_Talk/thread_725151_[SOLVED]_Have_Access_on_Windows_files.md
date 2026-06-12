---
title: "[SOLVED] Have Access on Windows files"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by TzaB on 2008-03-15
Hello all, i am running Windows XP and Ubuntu 7.10 with dual boot and i want to ask you a question. When i am with Ubuntu am i able to have access to the fIles that are in the partition of Windows?
If this is correct, then can you tell me how?
Thank you

---

### Post by taurus on 2008-03-15
Yes, you can access files on windows while you are in Ubuntu.  You just need to add an entry in /etc/fstab for windows partition so it would be mounted automatically each time you boot Ubuntu.

Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by dje on 2008-03-15
Yes you can, is there an icon on your desktop that looks like a hard drive labelled 'sda2' or similar? If so just double click to view all your windows files in nautilus. If there isn't open nautilus and in the sidebar there may be something such as '10G volume', double click that to view your windows files. If neither of these are applicable please post the output of this here:
```
blkid
```
To get the output just go to Applications >> Accessories >> Terminal and type the above command and hit return, then just copy and paste here

dje

---

### Post by glennric on 2008-03-15
Yes, you can access windows partitions.  You can use either ntfs3g or ntfs with fuse.  Find out what the device name of your windows partition is with
```
sudo fdisk -l
```
Look for NTFS for an indicator as to which one it is.  
Then to use ntfs-3g (for instance) do:
```
sudo apt-get install ntfs3g
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/??? /media/disk
```
where ??? is the device name of the partition found above.

---

### Post by TzaB on 2008-03-15
One minute to read the replies because i confused a bit :P

---

### Post by taurus on 2008-03-15
> **glennric said:**
> Yes, you can access windows partitions.  You can use either ntfs3g or ntfs with fuse.  Find out what the device name of your windows partition is with
```
sudo fdisk -l
```
Look for NTFS for an indicator as to which one it is.  
Then to use ntfs3g (for instance) do:
```
sudo apt-get install ntfs3g
sudo mkdir /media/disk
sudo mount -t ntfs3g /dev/???
```
where ??? is the device name of the partition found above.

The driver is ntfs-3g and shouldn't you need to include the mount point, /media/disk, when you try to mount it by hand?

---

### Post by glennric on 2008-03-15
> **taurus said:**
> The driver is ntfs-3g and shouldn't you need to include the mount point, /media/disk, when you try to mount it by hand?

You are correct, sir!  I fixed it above.

---

### Post by TzaB on 2008-03-15
Thank you very much for the help dudes :)
I did it.

---

