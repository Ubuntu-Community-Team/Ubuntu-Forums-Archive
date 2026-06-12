---
title: "ext2fs &amp; mac os x compatibility issues?"
date: 2007-07-20
forum: Apple PPC Users
---

### Post by phidia on 2007-07-20
I did a search here but the threads referencing ext2fs were pretty old and limited too.
I wonder if anyone uses the ext2fs program that puts a ext2 manager in the mac os x system preferences
I've found that program or fs manager to be unpredictable at best.
Mostly I use a homebuilt pc that I have ubuntu and a few other distros on. I also have a G4 powerbook running 10.3
I would like to share files between the pbook and my desktop through an external drive, but although I can mount a ext2/3 disc in osX with aforementioned utility transferring large files causes errors and even brings down the mac (wants to restart). The disc mounts and works fine in linux.
I didn't know where else to bring this up although osxhints is sometimes a good site for these questions-I just rarely use osxhints much anymore and I'm here often. The devs of ext2fs manager don't seem to have a webpage so I have no recourse there.
I'm sorry for the long post and it's so aggravating that I can't just transfer files between these two computers that I'm considering giving up the mac and just getting a pc laptop which I would run solely linux/ext3fs on of course.
I knew I could use vfat to format my external drive with but that does have some drawbacks (permissions not picked up) and without recompiling the kernel linux won't r/w hfs+ but you mac people know that. 
Are there any good and maybe simple options I'm overlooking?Thank You:)

---

### Post by stmiller on 2007-07-21
Linux can read and write to an HFS+ OS X drive, as long as journaling is turned off. 

No need to recompile the kernel (I *think*), just

$ sudo apt-get install hfsplus hfsutils

There is a good kernel compile how-to for x86 if you search for the Kernel Master Thread on this forum.

Write support with that ext2fs driver is experimental. Reading works great though. That entire project is done by one person alone, so that could be the reason for not getting much feedback on their mailing list.

---

### Post by Auria on 2007-07-21
be careful with ext2fs on OS X, even in read-only mode it caused me kernel panics

---

### Post by phidia on 2007-07-21
> **Auria said:**
> be careful with ext2fs on OS X, even in read-only mode it caused me kernel panics

I guess this is a user beware thing since there seems to be many online resources promoting ext2fsx.
Thanks very much for the responses. 

I had one other thought since i prefer ext3 or reiserfs to hfs+ and I already have formatted my external and use it with linux so I don't want to format it hfs+ now. I do appreciate knowing about linux's ability to r/w though.
My idea is a networked drive. A drive connected by Ethernet wouldn't have a file format compatibility problem-is that correct? Thanks again.

---

