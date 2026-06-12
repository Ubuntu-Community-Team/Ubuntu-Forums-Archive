---
title: "Mounting NTFS Windows Partition"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Justus on 2005-12-07
After much fooling around, I was finally able to mount my NTFS Windows partition, with an access point of users/justus/big-hd or something like that. Anyway, all the files are showing up, but I can't edit the files, or change the permissions, because it says it's a Read-only drive. :confused: 
What can I do to make it behave properly?

---

### Post by aysiu on 2005-12-07
You can't.
NTFS is read-only.
FAT32 is read/write.

---

### Post by Justus on 2005-12-07
Then how does Windows read/write to it? There's absolutely no way at all to read/write to it from Linux?

---

### Post by aysiu on 2005-12-07
[QUOTE=Justus]Then how does Windows read/write to it? There's absolutely no way at all to read/write to it from Linux?[/QUOTE] Windows is Windows. It can't write to Ext3, but Linux can. NTFS is a native Windows format. Ext3 is a native Linux format. FAT32 is a filesystem both can read from and write to.

---

### Post by Justus on 2005-12-07
Is there an advantage to NTFS over FAT32?

---

### Post by aysiu on 2005-12-07
[QUOTE=Justus]Is there an advantage to NTFS over FAT32?[/QUOTE] Yes. It doesn't fragment as badly as FAT32. It can hold files larger than 4 GB (handy if you burn DVDs). It supports file permissions. It's faster for XP.

Very typically, dual-booters will have one NTFS partition (for Windows XP), one FAT32 partition (to share files between Windows and Linux), and one Ext3 partition (for Linux).

---

### Post by Justus on 2005-12-07
[QUOTE=aysiu]Very typically, dual-booters will have one NTFS partition (for Windows XP), one FAT32 partition (to share files between Windows and Linux), and one Ext3 partition (for Linux).[/QUOTE]

Sounds like a good idea. Thanks!

---

### Post by BatsotO on 2005-12-07
As far as I know, the reason linux can't write to ntfs is that ntfs use different set of dll files (ntkernel or something).
If you want to have write acces you need to some how emulate this drivers. I heard some project called captive in sourceforge that can do this stuff. 
The only xp box in here belong to my boss so it's kind of risking my job if i try messing around with his hard drive:razz: 
please do try, I like to know how it works.

---

### Post by aysiu on 2005-12-07
As far as I know, every implementation of write-access to NTFS from Linux is **experimental** (i.e., don't use it!).

If you're curious, and don't mind borking your NTFS partition, Captive NTFS is [here](http://www.jankratochvil.net/project/captive/)

---

### Post by mdsmedia on 2005-12-07
I've heard the term "borking" a few times here. What does it mean?

---

### Post by Justus on 2005-12-07
Google doesn't have a definition for it ;)
You can pretty much figure out what it means from the context it's used in above though.

---

### Post by aysiu on 2005-12-07
[QUOTE=mdsmedia]I've heard the term "borking" a few times here. What does it mean?[/QUOTE] [http://www.urbandictionary.com/define.php?term=bork](http://www.urbandictionary.com/define.php?term=bork)

---

### Post by BatsotO on 2005-12-07
Thank you for pointing that out.
yes.. what is borking? I'm not native english speaker.
all i have with my previous ntfs was memory dumping.

---

### Post by mgmiller on 2005-12-08
Generally, borking means messing up or breaking something.  Not a good thing to do to your file system.
My understanding of the NTFS-linux problem is that NTFS is a journaling file system wherein the journal part is propriatery microsoft code.  It functions almost like a database in that any time you write to a file or create a new file, it changes an entry in the file system journal, which keeps track of everything.  Since linux can't write to the file system journal that tells the  file system what's going on because the code is "black boxed" by microsoft, if you do manage to write to the file, NTFS will lose track of it and won't know about the changes.  Or if you create a new file on the NTFS disk, the journal won't know it's there and will quickly overwrite it, or in creating the file, you may overwrite something else that is there or cause it to move to a different area on the disk or cause a little bit of fragmentation, etc.  that the journal won't know about.  The contents of the NTFS disk quickly get "borked".

By mounting the drive as read only, you can't mess up the journal.

Hope this helps.

---

