---
title: "What file system should I use for data partition?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by geezas on 2006-12-15
I made 1 gig for swap
20 gig for ubuntu
and the rest ~53 gigs for data (movies, music, pics, docs, etc)
what file system should I use?
if i use ext3 will this cause any problems when puting files with extentions that are for windows?  Plus I'm planning to hook up this computer with a windows one through a network.  Does it matter or not if i will be changing files back and forth with those two computers?

give me your thoughts on this, since i dont know whats better...
thanks

---

### Post by Kazna on 2006-12-15
Windows and Linux can both read/write to FAT32 formatted drives.

That seems best for you.

---

### Post by geezas on 2006-12-15
Thanks for the tip

what are the major differences between fat32 or ext3 ?

what happens when i want to move a file from fat32 partition to ubuntu partition?
will there be any slowdowns?  i.e. if i will be watching video, playing music or working on gimp. all the programs running from ubuntu partition, while working with files on fat32 partition...
Is there any change in performance?

---

### Post by patrick.dylan on 2006-12-15
> **geezas said:**
> Thanks for the tip

what are the major differences between fat32 or ext3 ?

The difference is that you can't write to ext3 from windows (without 3rd party apps and messiness).  Use FAT for a partition that will be used from both OS's.

---

### Post by szf on 2006-12-15
fat32 isn't much of a filesystem.

No, really, fat32 is good for interchange - but it's not "choice." It's up to you to decide whether interoperability trounces stability.

---

### Post by jdong on 2006-12-15
I've had terrific experiences with fs-driver.org's ext2/3 driver for Windows.

I prefer it much over a fat32 partition, which is not nearly versatile enough for today's usage.

---

### Post by geezas on 2006-12-15
what are the major differences between fat32 or ext3 ?

what happens when i want to move a file from fat32 partition to ubuntu partition?
will there be any slowdowns? i.e. if i will be watching video, playing music or working on gimp. all the programs running from ubuntu partition, while working with files on fat32 partition...
Is there any change in performance?


...how about, creating a small partition that will be used if i wanted to transfer any files to windows....  for example, i have the 50 gigs of ext3, and about 4 gigs of fat32.  Then if i want to transfer files to Windows PC, i move the files from ext3 to shared fat32 partition so windows can recognize it...
I think it sounds great, but what do I know...  What do you think guys?

---

### Post by Kazna on 2006-12-15
Basically thats all you need to know. Other formats will not let you use Windows and Linux to read/write to a HDD.

A word of warning I'd like to add, for us used to Windoze with undeleting deleted files, in the words of  one of the developers Andreas Dilger: [I]> In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.[/I]
  *Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.*


If you delete something on this format drive (ext3), its not recoverable at all.

---

### Post by po0f on 2006-12-15
geezas,

For network transfer, it doesn't matter what filesystem you use.  As long as Windows is able to connect to the box, you can get to the shared files.  Note that I don't stream my media, my experience is based solely off data sharing.

---

### Post by Kazna on 2006-12-15
[b][FAT32 File System](http://support.microsoft.com/kb/154997)

[EXT3 File System](http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html)[/b]

---

### Post by geezas on 2006-12-15
poof,
so you're saying I can have my data partition in ext3 format and windows will be able to at least read the shared files from that partition?
What do you think of my idea of creating of a small fat32 partition used specifically for sharing files between the systems.  Like a common ground where I can create, put, edit, and read files from either one of the computers.

---

### Post by po0f on 2006-12-15
geezas,

You could do that, but it would be almost pointless as the sharing is over the network.  You can setup a private FTP server on your Ubuntu box and Windows will have no problem uploading to it.  There are more elegant solutions available though (namely, Samba).

---

### Post by geezas on 2006-12-15
OK, thanks for the answer... for now, small fat partition will be ok, once I'll get a better understanding of this new OS, I will do things better ;]

---

### Post by GameManK on 2006-12-15
As already mentioned, if you're sharing over the network you DO NOT NEED a FAT partition.  For network sharing, it doesn't matter at all what the file system since the OS you're running on the computer you're sharing from is the one doing the reading and writing.

When you might need a FAT partition or ext2/3 drivers for windows is if you dual boot.  As in, when you need windows to directly access the drive.

---

### Post by Kazna on 2006-12-16
Thats all correct, but if you have it in FAT32, you can link the HDD onto any Linux and Windows system and read/write/copy/delete data whereas you cannot otherwise. Thats why I was offering the shorthand solution.

---

### Post by hyper_ch on 2006-12-16
If you want to share over the network use samba to create a network share on your linux box...

---

### Post by Kazna on 2006-12-16
BTW I just remembered, Fat32 has a max size per file of 4GB.

---

