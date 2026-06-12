---
title: "brand new harddrive."
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by doctapeppa on 2008-02-01
What filesystem should I format it as? I will mainly use it for storage of movies (these may be streamed). Is there any disadvantage to using NTFS on it so that I can see it from my windows install? 

Frank

---

### Post by wolfen69 on 2008-02-01
you could format it fat32. that way ***any*** OS will be able to see it.

---

### Post by PinkFloyd102489 on 2008-02-01
If you set up Samba and point the share to the drive, you can access it from Windows without formatting to NTFS. Personally, Id go with ext3 or ReiserFS, as those do not fragment like FAT and NTFS. This means less errors and less hassle for you.\


EDIT: Misread your post. Go with NTFS if you're accessing from a dual-boot with Windows.

---

### Post by asmoore82 on 2008-02-01
NTFS is incapable of storing UNIX file permissions, which can cause some oddities on GNU/Linux systems.
There is also a Free ext3(Linux filesystem) Driver for WinXP that I hear works perfectly.

---

### Post by articpenguin on 2008-02-02
> **PinkFloyd102489 said:**
> If you set up Samba and point the share to the drive, you can access it from Windows without formatting to NTFS. Personally, Id go with ext3 or ReiserFS, as those do not fragment like FAT and NTFS. This means less errors and less hassle for you.\


EDIT: Misread your post. Go with NTFS if you're accessing from a dual-boot with Windows.

avoid reiserfs. Its an unreliable filesystem and its future is uncertain as hans reiser is in jail.

---

### Post by bruce89 on 2008-02-02
> **articpenguin said:**
> and its future is uncertain as hans reiser is in jail.

Interesting reason.

I'd use FAT32 if it needs to work with Windows also, ext3 otherwise.

---

### Post by articpenguin on 2008-02-02
ext3 is horrible at deleting large files. JFS deletes much faster and it is also a lot better with large files than ext3 is. 

Fat32 has a file size limit of 4Gbs

---

### Post by bruce89 on 2008-02-02
> **articpenguin said:**
> ext3 is horrible at deleting large files. JFS deletes much faster and it is also a lot better with large files than ext3 is. 

Fat32 has a file size limit of 4Gbs

I suppose something more nice with dealing with large files would be a good idea. If it's only used for videos, it's good.

---

### Post by netscribe on 2008-02-04
In my experience, formatting it to NTFS for the multi-boot works well.  The only thing I had to worry about was getting a listing in my /etc/fstab and self-mounting the volume after bootup.  I found that letting Ubuntu do it for me was not working out as well.   This is not to say you cannot rely on Ubuntu to mount correctly... I just have many encrypted files that are 100 MB to 25 GB in size, so the auto-mount option not working might be specific to that. 


1)  So I make sure the volume is listed in fstab:

/etc/fstab:

# /dev/sdb1
UUID=49F1-A011  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1



2)  Then, when I'm wanting to use it, I write:

mount -t ntfs /dev/sdb1 /usr/netscribe/somefolder/wherever-you-want


then, I make sure I dismount it when I'm done or before I shutdown.  Hope that helps.

---

