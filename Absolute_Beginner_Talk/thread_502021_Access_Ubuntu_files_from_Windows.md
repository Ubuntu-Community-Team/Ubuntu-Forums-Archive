---
title: "Access Ubuntu files from Windows?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by RangerDanger on 2007-07-16
I have searched and only seem to run around in circles.  What is the best and simplest way or program to access my ubuntu files from my windows install.  I have a dual boot set up that seems so far to be running with no hitches.  I still have some tweaking and a lot of discovering to do.  I have chosen not to use a shared partition and instead want to access each install from the other.  Mostly just want to be able to reach documents, photos, music and videos.  Thanks for any help guys.

---

### Post by aysiu on 2007-07-16
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by freesitebuilder on 2007-07-16
To read files I use(d) Linux Reader [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by jingo811 on 2007-07-16
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
This one helped me in an instance when I couldn't acceess /root partition with Ubuntu LiveCD.
Just extract the .zip file and click on the .exe and you're up and running.

But you probably can't read the files in Windows directly...it's one of those S.O.S tools.

---

### Post by Don Cox on 2007-07-16
> **aysiu said:**
> [http://www.fs-driver.org](http://www.fs-driver.org)

How reliable is this small application? Searches in Google plus groups suggest that using it is not 100% straightforward. Currently my NTFS configuration tool works flawlessly, permitting read and write access to Windows files from Ubuntu; would it be risky to attempt the reverse using Ext2 IFS to access Ubuntu files from XP Home while the NTFS tool is still installed? Put another way, can these two applications be safely used together?

---

### Post by RangerDanger on 2007-07-16
> **Don Cox said:**
> How reliable is this small application? Searches in Google plus groups suggest that using it is not 100% straightforward. Currently my NTFS configuration tool works flawlessly, permitting read and write access to Windows files from Ubuntu; would it be risky to attempt the reverse using Ext2 IFS to access Ubuntu files from XP Home while the NTFS tool is still installed? Put another way, can these two applications be safely used together?

This is a very good question and I would love to know the answer as well.

---

### Post by testube_babies on 2007-07-16
> **Don Cox said:**
> How reliable is this small application?

I've used the fs-driver in both XP and Vista and it's never given me any troubles whatsoever.  I highly recommend it, since it mounts your ext drives just as it would a native filesystem.

I also use the ntfs-3g driver in Linux, there are no problems running the two side-by-side.

---

### Post by Don Cox on 2007-07-18
Ext2 IFS, as recommended above, works well enough. However, for convenience, files written in Ubuntu with OO Word Processor are maybe better stored as .doc rather than .odt files if subsequent access to the latter from Windows is required. 

Please see: [odf-converter.sourceforge.net]("odf-converter.sourceforge.net") for a possible alternative approach. Any experience anybody?

---

