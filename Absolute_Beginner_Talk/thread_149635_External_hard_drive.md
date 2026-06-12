---
title: "External hard drive"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by nsmith on 2006-03-24
I just installed Ubuntu operating system on my PC.  I have an external hard drive that has many documents/music/programs/videos.  When I try and write to my hard drive I get a message that says I do not have permission.  I also cannot play music or films.  Is there a simple solution to this problem? :-k

---

### Post by pbaehr on 2006-03-24
Are you mounting the drive manually or is it being done automatically for you? Also, do you happen to know what file system the hard drive uses? NTFS? fat32? ext3?

---

### Post by gigi1234 on 2006-03-24
Assuming your file system is not NTFS wouldn't a quick fix be to go to the terminal and start Nautilus:

$ sudo nautilus

This is what I do since I haven't figured out how to permanently change the permissions.

---

### Post by pbaehr on 2006-03-24
Opening nautilus won't override the permissions, though.

And to permanently change permissions on a mounted drive you need to edit /etc/fstab.

---

### Post by nsmith on 2006-03-24
My external hard drive is NTFS formatted and it is being mounted automatically.   
My Pendrive is a FAT32 format and seems to do just fine.  I can read documents on my external hard drive but if I try and creat folders or move documents around or simply modify the document I am not able to.

---

### Post by pbaehr on 2006-03-24
Okay. NTFS is read only from Ubuntu. Apparently it can't safely write to an NTFS partition. There are ways to circumvent this, but I've never tried and I've heard they're not without their risks.

---

### Post by nsmith on 2006-03-24
pbaehr,

Are you suggesting that I reformat my external hard drive?

I still have the problem of not being able to play DVDs or listen to MP3 files on my system.  Any help?

---

### Post by pbaehr on 2006-03-24
If you use the external drive on a computer that runs something other than Linux you could reformat it to FAT32 so that both could access it. Or, if you're Linux only now you could use ext3. They will both allow you read and write access. This of course assumes that you have somewhere to back up your data while you do it as it will destroy anything currently on the disk.

I didn't notice the other bit about not being able to play mp3s or watch DVDs. The codecs don't come with Ubuntu by default for some sort of legal reasons. Check out how to install them here:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by nsmith on 2006-03-24
Thanks for the help :D

---

### Post by pbaehr on 2006-03-24
No problem. Come back if you need more of it. You'll find it in abundance here.

---

