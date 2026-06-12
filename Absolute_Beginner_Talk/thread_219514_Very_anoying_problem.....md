---
title: "Very anoying problem...."
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2006-07-20
I have a San-Disk cruzer mini 512mb USB memory stick. I plug it into my desktop's USB port. I can open the stick and view the files. I can copy files, not cut, to my desktop. I can't paste anything or write to this stick. What can I do to fix this? I have rebooted. Changed USB ports. No luck...
There is no write protection on the stick that I can see either....

---

### Post by Crosbie on 2006-07-20
How is it formatted?  FAT?  FAT32?  Or something else?

---

### Post by crystal on 2006-07-20
hmm... I believe I have the same problem with my Imation 1 GB thumb drive on Dapper Drake. It works under MS Windows, but write operations to it on Linux seem to have no effect, even though they do not fail with an error message.

---

### Post by risbac on 2006-07-20
Could be an NTFS formatted partition. Then you can only read it, not write to it. In this case, you don't have many choices:

-you wait for the read/write driver. It should arrive in the next version of Ubuntu, but not sure at all. So could take some time
-you reformat your memory stick in FAT32 format. Not the best format, will fragment, but compatible with both Windows and Linux
-You format with another file system (like ext3), but then Windows may not read it, so it's not the solution for a portable storage.

---

### Post by crystal on 2006-07-20
Ah, okay. That sounds logical.

---

### Post by risbac on 2006-07-20
Well, FAT is really the most common file system on USB sticks though... As third party hardware can't write to NTFS, it's better to have a FAT FS, for basic compatibility reasons. It's weird that you can't write to those sticks. I'm curious to see if they are really NTFS or if it's something else.

---

### Post by dragon1964m on 2006-07-20
Thank you for reminding me about format! I rebooted in windows, offloaded all files. Rebooted into Linux and was able to write to the stick.
Looks like files don't mix well. :-D

---

### Post by crystal on 2006-07-20
> Well, FAT is really the most common file system on USB sticks though... As third party hardware can't write to NTFS, it's better to have a FAT FS, for basic compatibility reasons. It's weird that you can't write to those sticks. I'm curious to see if they are really NTFS or if it's something else.
System monitor tells me that it is formatted as vfat.

---

### Post by risbac on 2006-07-20
> Looks like files don't mix well. 

Normally, it doesn't really matter what kind of files you want to put there, it's the FS that matters. But as long as it works now, it's the most important!

Crystal, VFAT is FAT, you should be able to write on it. Are u sure the files on it don't belong to someone else? Maybe a "sudo nautilus" will allow you to delete the file. I had the same problem on my walkman, I was able to put files, but not to delete them, as I was using two different computers to write on it, and thus placing files belonging to two different users...

---

### Post by crystal on 2006-07-20
> Crystal, VFAT is FAT, you should be able to write on it. Are u sure the files on it don't belong to someone else? Maybe a "sudo nautilus" will allow you to delete the file. I had the same problem on my walkman, I was able to put files, but not to delete them, as I was using two different computers to write on it, and thus placing files belonging to two different users...
sudo did not work either. I will probably try dragon1964m's accidental solution later.

---

