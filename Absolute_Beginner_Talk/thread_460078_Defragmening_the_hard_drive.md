---
title: "Defragmening the hard drive"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by wil313 on 2007-05-31
I know with Microsoft you have to continuously defragment the hard drive. Do you have to do this with linux?

---

### Post by reckless2k2 on 2007-05-31
The linux file system does not need such a process to take place.

---

### Post by wil313 on 2007-05-31
Ok, thanks a lot.

---

### Post by ncappel1 on 2007-05-31
This is a good question, can someone please explain, in a nutshell, why?

---

### Post by Malibu Illusion on 2007-05-31
They do not need defragmenting because they're designed to minimize fragmentation in the filesystem during operation by default; they're more efficient at storing things than an NTFS filesystem, for instance, and a billion times more efficient than a FAT system

That's a very basic and simple 'nutshell' reason. :)

---

### Post by teknosexual on 2007-05-31
> **ncappel1 said:**
> This is a good question, can someone please explain, in a nutshell, why?

Here is a writeup I found that explains how Linux writes to EXT filesystems: [Why doesn't Linux need defragmenting?]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

If  you're using FAT32, it sounds like you would experience some fragmentation. What about having NTFS and EXT3 on the same hard drive? Would one side get fragmented? Would defragging the NTFS partition affect the EXT side?

---

### Post by Malibu Illusion on 2007-05-31
> **teknosexual said:**
> If  you're using FAT32, it sounds like you would experience some fragmentation. What about having NTFS and EXT3 on the same hard drive? Would one side get fragmented? Would defragging the NTFS partition affect the EXT side?

The partitions would be treated separately and behave exactly as they would independently because, for all intents and purposes, they are independent.

---

### Post by candtalan on 2007-05-31
One Nutshell coming up - from a non expert!

Windows puts stuff onto the hard drive into an earliest space, getting pretty snug all round. Data things change, and the get snug approach gets pretty complicated to fit all the small gaps etc. This needs outside help to unravel.

Linux (Unix?) file systems puts stuff into a (random??) large space up the drive somewhere. Lots of space in front, lots of space behind. Not at all snug but it works great! 

It means that while there is some unused space in the drive (up to say 80% full or so?) then the built-in elbow room works to sort itself out. When you delete a file, its space and its surrounding space are again available as a - 'large' useful space. As I understand it the random approach will generally provide self unfragmenting - or at least will not get fragmented by design, which is what windows seems to get.

hth

---

### Post by MeeMaw on 2007-05-31
The NTFS and fat32 file systems file everything "all crammed together" and then when you access a file and change the size of it, the system has to put part of it away where it was stored and the rest of it away somewhere else...... hence the reason for defrag. (If you've ever noticed the difference between the starting and the finished defrag, you'll see what I mean.)  

In Linux, file storage is handled differently to account for the difference in file size (as described by candtalan), so files can be put back where they came from, and all together instead of in pieces.    

If you have two partitions (one Linux, one NTFS) the NTFS will still need to be defragged, but not the Linux ext3.

Hope we all clarified it for you!  ;)

---

### Post by jrusso2 on 2007-05-31
> **candtalan said:**
> One Nutshell coming up - from a non expert!

Windows puts stuff onto the hard drive into an earliest space, getting pretty snug all round. Data things change, and the get snug approach gets pretty complicated to fit all the small gaps etc. This needs outside help to unravel.

Linux (Unix?) file systems puts stuff into a (random??) large space up the drive somewhere. Lots of space in front, lots of space behind. Not at all snug but it works great! 

It means that while there is some unused space in the drive (up to say 80% full or so?) then the built-in elbow room works to sort itself out. When you delete a file, its space and its surrounding space are again available as a - 'large' useful space. As I understand it the random approach will generally provide self unfragmenting - or at least will not get fragmented by design, which is what windows seems to get.

hth

To me this would seem to be the definition of fragmentation which is storing files in non-contiguous areas's on the disk.

Maybe Linux ext3 is fragmented but its performance is not effected as much by it?

---

### Post by sessine on 2007-05-31
> **jrusso2 said:**
> To me this would seem to be the definition of fragmentation which is storing files in non-contiguous areas's on the disk.

Maybe Linux ext3 is fragmented but its performance is not effected as much by it?

No.  The fragmentation on an NTFS system is that the data that makes up a given file (e.g. Word document) is spread out across the drive e.g. part of the file may be at the begining of the drive, some more in the middle and more still out at the edge.  On a Linux ext3 filesystem the files may be spread out but all the data for a given file is in the same, continuous, area.

---

### Post by hasimir44 on 2007-05-31
"fragmented" is referring to individual files - so as long as the individual files are stored together, then they are not fragmented.. 

I'm curious as to how ext3 (or reiserfs) would handle this scenario: 

your partition is 99% full, but there are small chunks of free space that add up to just enough for a new file - would ext3/reiserfs split up the file?

---

### Post by DreamcastJack on 2007-05-31
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

that website explains everything you need to know.:popcorn:

---

### Post by teknosexual on 2007-05-31
> **Malibu Illusion]
The partitions would be treated separately and behave exactly as they would independently because, for all intents and purposes, they are independent.[/quote]

[QUOTE=MeeMaw said:**
> If you have two partitions (one Linux, one NTFS) the NTFS will still need to be defragged, but not the Linux ext3.

Hope we all clarified it for you!  ;)

Yep, that is good to know! Thx.

---

