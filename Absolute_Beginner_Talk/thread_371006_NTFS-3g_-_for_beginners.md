---
title: "NTFS-3g - for beginners?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by andrewlinn957 on 2007-02-26
I'm new to ubuntu, so would using NTFS-3g be advised or should i just make a FAT32 partition for sharing stuff?

Does NTFS-3g mean that while in Ubuntu i can read from and write to an NTFS partition, but will still need a driver like [FS-Driver ]("http://www.fs-driver.org/")to be able to read from and write to my ubuntu partition while in windows?

Also, is using Fs-Driver recommended?

And just to be clear, does NTFS-3g only enable ubuntu to read from and write to NTFS, or does NTFS-3g actually convert your linux partition to the NTFS file system?

Thanks alot.

---

### Post by Maestro23 on 2007-02-26
NFTS-3G: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

Should help you.

---

### Post by bodhi.zazen on 2007-02-26
ntfs-config = ntfs-3g made easy

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by wonk-o-matic on 2007-02-26
If you're using edgy, and you have the "universe" repository working, just "aptitude install ntfs-3g".  It's a bit more painful to install in earlier versions of Ubuntu.  

ntfs-3g  doesn't change your Linux partition, and it doesn't change the way that Windows looks at your Linux partition.  It only gives the ability to read and write Windows files from the Linux operating system.  

The only thing that I can think of that might bite a noob is the fact that Linux treats filenames in a case-sensitive mode, while Windows does not.  A friend has mentioned that two files with the "same" name in Windows (such as "file.txt" and "FILE.TXT") doesn't corrupt anything (I haven't tried it) but I'm not sure which one Windows would actually open.

I just realized that setting up ntfs-3g in your /etc/fstab file might not be obvious.  Here's an example:
        [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

If you're on edgy, search the doc for fstab - the rest of the stuff is probably not important to you.

---

