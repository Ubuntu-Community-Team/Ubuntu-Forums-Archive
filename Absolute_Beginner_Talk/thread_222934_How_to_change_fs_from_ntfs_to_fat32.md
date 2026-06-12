---
title: "How to change fs from ntfs to fat32?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by BlueStreak on 2006-07-25
In my pre-linux days I bought a 200 GB external hard drive for backup/data storage.  Being an XP user at the time I formatted it NTFS.  So as you know writing to it from linux is a problem.

Can I change it to fat32 via Ubuntu while keeping data intact?

---

### Post by T700 on 2006-07-25
> **BlueStreak said:**
> Can I change it to fat32 via Ubuntu while keeping data intact?

I've not ever seen a way to safely do so.  Sorry; hope someone shows me wrong.

Paul

---

### Post by Drakkor on 2006-07-25
Afraid T700 is right to change it you must reformat it.

---

### Post by BlueStreak on 2006-07-25
Well if it can't be done safely, I've got plenty of space so I'll just make a new partition if I have to

---

### Post by BlueStreak on 2006-07-25
Thanks for the responses.  Let me know if this will work:

image the drive to dvds with Acronis True Image, reformat to fat32 then restore the image from the dvds

Sound dangerous?

---

### Post by Drakkor on 2006-07-25
When you restore the image,won't it still be ntfs ?? :-k

---

### Post by BlueStreak on 2006-07-25
not sure about that.  would it be if the drive is formatted fat32?

---

### Post by Drakkor on 2006-07-25
Yeah,I'm pretty sure that Acronis wipes the file system and anything on there to restore what you had on there originally,ie: an "exact copy" of what you had before. ;)

---

### Post by VirtuAlex on 2006-07-25
You have fairly big drive, why don't you just resize ntfs, make fat32 partition and copy everything there. Then wait for a while. Ntfs rw support is coming (in fact some people already use it). And who knows, maybe after a while you'll reformat everything to ext3 and forget about ntfs and fat32 altogeter with windows.

---

### Post by mwshook on 2006-07-26
Is Fat32 fairly compatible between ubuntu and XP? I'm wanting a partition that can be shared between the two OS's

---

### Post by Jagot on 2006-07-26
> **mwshook said:**
> Is Fat32 fairly compatible between ubuntu and XP? I'm wanting a partition that can be shared between the two OS's

Yes

---

### Post by Aurdal on 2006-07-26
Windows XP only supports fat32 disks up to 32 GB in size though.

---

### Post by Wahngrok on 2006-07-26
> **Aurdal said:**
> Windows XP only supports fat32 disks up to 32 GB in size though.
Not quite. 32 GB ist the XP **formating** limit for FAT32, not the limit XP can handle (which is about 8 TB). ;) 

Info from:
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;q314463](http://support.microsoft.com/default.aspx?scid=kb;EN-US;q314463)

---

### Post by Aurdal on 2006-07-26
Glad to hear that. :) But then again if I knew that back when I was dual-booting I might have still had Windows... :o

---

### Post by moma on 2006-07-26
Sharing a partition between linux & windows.
o--> [http://ubuntuforums.org/showthread.php?p=1278632#post1278632]("http://ubuntuforums.org/showthread.php?p=1278632#post1278632")

---

