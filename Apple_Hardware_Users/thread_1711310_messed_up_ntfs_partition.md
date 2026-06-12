---
title: "messed up ntfs partition"
date: 2011-03-21
forum: Apple Hardware Users
---

### Post by ichigo on 2011-03-21
Hi,

I'm running a multi-boot configuration of OSX and Ubuntu on my macbook. I usually put all my data on a shared NTFS partition (when I set up the system this looked like the most advanced format both OS support rw).
However, it seems like something went terribly wrong and the file system is (partially) corrupted. I don't know what exactly I did to cause this, but some filenames seem to point to other files than they did before. E.g., when I open file A, the content of file B is displayed. When I try to delete file A, I get the error that file A doesn't exist.

I've tried to fix this by running 
```
sudo ntfsfix /dev/sda3
```
which returned
```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda3 was processed successfully.

```
but didn't change a thing. Does anybody have an idea how to fix this? I was hoping to recover the files somehow, because my last update is 5 weeks old...

Btw, applications that may have caused the trouble are (to my knowledge) eclipse, cmake and backintime (->rsync)

---

