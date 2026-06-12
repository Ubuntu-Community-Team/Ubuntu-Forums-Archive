---
title: "How do I get Ununtu to write to external drives previously used with Mac?"
date: 2009-07-04
forum: Apple Hardware Users
---

### Post by tomreid on 2009-07-04
Hi

I have two external Lacie drives I've previously been using with Macs. 

I am transitioning over to Ubuntu, but Ubuntu can only read from and not write to these drives. 

I found this old post here that seems to answer some of the questions:

[http://ubuntuforums.org/showthread.php?t=353475](http://ubuntuforums.org/showthread.php?t=353475)

At this time the Ubuntu driver for NTFS was in Beta. Is there any easy way now I can get Ubuntu to both read and write to these drives?

cheers

---

### Post by Idefix82 on 2009-07-04
Do you know for sure that the drives are formatted as ntfs? Can you mount one of them, then open the terminal, type in
```
ls -l /media
```
and paste the output here?

The current ntfs driver in Ubuntu usually has no problems with writing to ntfs, so I am suspecting that it's just a permission issue, in which case it will be a one line fix.

---

### Post by tomreid on 2009-07-05
Yes I could be wrong about NTFS, here's the output of that command:

cheers

tom@tom-macbookpro:~$ ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2009-06-03 16:06 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-06-03 16:06 cdrom0
drwxr-xr-x 1 root root   42 2009-07-03 09:09 LaCie
tom@tom-macbookpro:~$

---

### Post by Idefix82 on 2009-07-06
Yes, it's a matter of permissions. The drive you want to access is owned by root (the so-called super user) and the permissions are such that only the owner can write to the drive. Do you only have data on the drive or is any part of the operating system on it, too? If it's just data, then you can just make yourself its owner:
```
sudo chown -R $USER:$USER /media/LaCie
```

That will deal with the one you had mounted when you posted your answer. Do the same for the other drive, substituting its name accordingly.

---

### Post by tiresia on 2009-07-06
Most probably the problem is not permission related but has to do with the FileSystem.
Did you format the HardDrive with the Apple Disk Utility? If so, you formatted it most probably with HFSPlus Journaled. Linux can read and write HFSPlus FileSystem, but can only read HFSPlus Journaled.
Therefore if you want to be able to write on that HardDrive, you should disable Journaling - what you can do only in MacOSX. Is MacOSX still running on your Mac?

The other option would be to format the HD - if you don't have any data on it!!!

---

### Post by cyberdork33 on 2009-07-06
yea, unless you are planning to use them primarily on the Mac, I would migrate to a new filesystem.

---

### Post by tomreid on 2009-07-06
Hi

I thought it may be a file system issue, I bought the Lacie drives from the Apple Store, didn't format them at all, they just worked when I used them with the Macs, so I didn't change the format at all. 

Ideally, what format do I change the drives to to use on Ubuntu?

cheers

---

