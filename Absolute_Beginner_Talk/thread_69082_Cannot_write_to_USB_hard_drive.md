---
title: "Cannot write to USB hard drive"
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by lilr0x on 2005-09-25
Basically I have a WD 200GB split in to two more or less equal partitions plugged in via USB2 from an enclosure.
These partions were formatted in _windows_. I do not want to lose over 100GB of files to get it to work on linux and I want these partitons to work in Windows (XP).

Basically if I try to create a new folder or drag files from my /bin/ folder (or any other folder) it just says "Could not write....".
I cannot change the permission of the drive/s from "Owner: Can View Content" to 
"Can View & Modify Content".

My theories right now are:
1. The files cannot be transfered because of a different file system when transfering from hard disk to NTFS partitons.

2. I am not mounting the drive properly.

3. Obviously the permission of the drives plays a huge part in this. Don't know why it does that.

---
fstab content
/dev/sda1	/mnt/usbhddp1	auto	noauto,owner,user,rw,umask=0 0 0 
/dev/sda2	/mnt/usbhddp2	auto	noauto,owner,user,rw,umask=0 0 0 
---
info center says the same as fstab.

That's about as much detail I can say. I hope I gave the correct info.
Anyone know what I can do?

---

### Post by mlomker on 2005-09-25
>  
/dev/sda2	/mnt/usbhddp2	auto	noauto,owner,user,rw,umask=0 0 0 


You don't have enough zero's there.  I also would not use auto if you know the file system type.  If it's a Windows drive then it's either vfat or ntfs.  NTFS drives are read-only in Ubuntu.

Look at [this post.](http://ubuntuforums.org/showpost.php?p=355988&postcount=8)

---

### Post by lilr0x on 2005-09-25
So I should make it NFTS and not auto?

I'm not on Ubuntu right now. I'm using suse 9.2.


And whats the about the zeros?

---

### Post by mlomker on 2005-09-25
> So I should make it NFTS and not auto?

If it is NTFS then that's your problem.  It is not writable in Ubuntu.

> 
And whats the about the zeros?

Look at the link that I gave you.

---

