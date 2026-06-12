---
title: "Dual boot question"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Fleece Flamingo on 2008-01-06
I am writting this from the live cd of gutsy and I want to know if you can make a /home partition that is usable for both Windows and Ubuntu? I tried using fat32 and it tells me

"The file system type fat32 cannot be mounted on /home, because it is not a fully-functional Unix file system. Please choose a different file system, such as ext2"

And so far I have a / partition of 2400mb
and a /home 120360mb
and a swap of 3100
Is this good?

---

### Post by PeterJS on 2008-01-06
There are ext3 drivers for windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
The page says ext2, but ext2 and 3 are compatible and interchangeable 3's just more resilient in case of a crash.

---

### Post by Fleece Flamingo on 2008-01-06
So I could use a ext3 partition and windows can browse it too?

---

### Post by eternicode on 2008-01-06
If you install the drivers, yes, windows could browse your ext3-based /home, but it's generally not recommended.  The most common way to go is to set aside some space (a few GB, depending on the type of usage) for a shared FAT32 partition between the OSes.  That way, both can natively access the data, but still be independent of each other.

---

### Post by Fleece Flamingo on 2008-01-06
but ubuntu wont let me make a /home folder fat 32
Oh well, I guess it's good to have a ext3 /home for updating ubuntu
Thanks for your help!:)

---

### Post by eternicode on 2008-01-06
> **Fleece Flamingo said:**
> but ubuntu wont let me make a /home folder fat 32

lol, no, a *separate* partition to share between the two.  A partition that won't be used for anything other than allowing both OSes access to certain files.

---

### Post by Blutack on 2008-01-06
You'll have to use ext3 for /home
However, there's nowt stopping you having a shortcut (or even mounting) your Windows "My Documents" in your home folder, and working on documents and stuff from there.

---

### Post by barney385 on 2008-01-06
root home swap
 
That's what swap is for...

---

### Post by eternicode on 2008-01-06
um....swap is to linux as the pagefile is to windows.

*id est*, you can't put files in it yourself :p

However, you could use Blutak's suggestion.  Set your windows partition to mount at boot, then put a symlink (shortcut) to it in your home directory (or desktop, etc)

---

