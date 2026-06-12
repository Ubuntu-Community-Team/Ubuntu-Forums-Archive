---
title: "Sharing a directory with Windoze"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-06-27
I've decidedI need windows after all (unfortunatly) for gaming if nothing else (And a few applications which just work better/are more polished on windows). However, I want to have all my homework, music and other stuff in a folder that both Windows and Unbuntu can access. 

I know fairly well how to make a third partition that'll hold all that (install windows, then run the Unbuntu disk, make a FAT32 partition, and let Ubuntu split up the rest). 

My questions are:

Where will this partition show up in Ubuntu?
Can I have my /home directory be my partition (or is that even worth it?)
Anything else I should be aware of before I start (I know to back up my stuff, that goes without saying).

---

### Post by aysiu on 2006-06-27
It'll show up wherever you mount it.

I would advise against making the /home partition FAT32. You can always mount the FAT32 partition within the /home directory if you want it more accessible.

You should be aware that you don't actually have to use a FAT32 partition. You can use Ext3 (your actual /home directory) and read/write it from Windows with this driver: [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by Amablue on 2006-06-27
What's the difference between Ext3 and FAT32?

And also, let me make sure I'm understanding you correctly. If I were to simply install Windows and Linux, I'd still be able to access my files stored on my linux paritition via that driver. Is that correct?

---

### Post by ubuntuuser on 2006-06-27
[quote=Amablue]What's the difference between Ext3 and FAT32?

And also, let me make sure I'm understanding you correctly. If I were to simply install Windows and Linux, I'd still be able to access my files stored on my linux paritition via that driver. Is that correct?[/quote] The main and most important difference is that FAT32 doesn't support file permissions, owner information and so on. The point in creating your personal /home/username directory is that you and only you (and root) have full read-write-execute permissions. If you make your /home partition FAT32, basically anyone would have full permissions on the whole partition. Another difference is that the ext3 blocksize is significantly smaller (512 bytes) than the FAT32 blocksize (4 kB I think). And I think that files on a FAT32 partition may not be larger than 4 GB.

Btw, I once used another ext3 driver, I think it was explore2fs, under WinXP. It worked fine, but soon after that my /-partition had some errors that could not be corrected. I don't know if explore2fs was causing this, but be warned.

---

### Post by Apple 101 on 2006-06-27
There are many ext2/3 read/write for Windows programmes around.  You can use them if you don't want a FAT32 partition, but then you run the risk of corruption, as said by ubuntuuser.

---

### Post by Amablue on 2006-06-28
Okay, I gave Ubuntu and Windows 10 gigs, and left about 35 gigs for them to share. However, I can't write to my /shared directory (that's where I put it). Is there a way to change the permissions, or did I do something wrong?

---

### Post by aysiu on 2006-06-28
FAT32:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Ext3:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by Amablue on 2006-06-28
I <3 you, aysiu. You're awesome. :mrgreen:

---

### Post by Amablue on 2006-06-30
Sorry for the double post, but I don't think editing my previous one will bump it to the top, and I don't think this question deserves it's own topic:

The driver provided works great with one small annoyance. In windows, when something is deleted from my shared parititon (E:) it is sent to a folder in e:\Recycled. When I try to delete stuff from there, it appears to be deleted, but when I refresh the folder it's still there (although, I did notice that it also appears in the regular recycle bin, and when I empty it the e:\Recycled is emptied too). 

Is there a way to change this behavior, or is the an issue with windows and not the driver? Ideally, I'd like to have things either just deleted, sent to the recycle bin and skip that e:\Recycled folder, or go to the .trash-alex folder.

---

### Post by Apple 101 on 2006-07-01
If you are in Windows and that happens (it never happens to me) open notepad and save the blank file.  Delete the file and empty the recycle bin to clear it.

---

