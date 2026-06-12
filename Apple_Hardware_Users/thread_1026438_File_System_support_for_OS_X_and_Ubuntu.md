---
title: "File System support for OS X and Ubuntu"
date: 2008-12-31
forum: Apple Hardware Users
---

### Post by DanielCarrera on 2008-12-31
Hello,

I have an external disk which I want to access from both Ubuntu and Mac OS X. In it I'll store backups, work documents and other files that I'd like to access from either OS. Thus, I must format it with a file system that both Ubuntu and OS X understand. The "obvious" choice is FAT32, but I really hate how FAT32 wrecks the Unix permissions.

Is there another, more Unix-like file system that Ubuntu and OS X both support? The goal is native read+write support, but I could settle for using a separate tool as long as it has read+write support. I'm looking at UFS, but I hear that Linux doesn't support it well because each Unix vendor has made its own changes to UFS. Does anyone know if that's true?

Can anyone suggest a file system that might fit my needs?

Thanks.

---

### Post by pxwpxw on 2008-12-31
You could try hfsplus i.e. macos extended.

---

### Post by DanielCarrera on 2008-12-31
> **pxwpxw said:**
> You could try hfsplus i.e. macos extended.

I thought that writing to HFS and HFS+ was "experimental" and not recommended. Though I haven't found any definitive information. Just some old-ish forum posts. I just did another search and [this thread](http://forum.oscr.arizona.edu/showthread.php?t=5168) seems to indicate that writing to HFS (ie. the non-journaled one) is ok.

I'd like to stay within the "recommended" solutions. Some of the files I plan to store will be important to me and I'd rather not hose the disk.

---

### Post by mkvnmtr on 2008-12-31
I believe there are some programs to install like macutils or some others to help but I have no trouble reading my mac formated files on my Ubuntu. In fact on my external hard drive I reformated to to mac hfs+ to be sure everything be read by both. In synapic go through the cross platform sections. You will probably find some other apps that are useful.

---

### Post by DanielCarrera on 2008-12-31
> **mkvnmtr said:**
> I believe there are some programs to install like macutils or some others to help but I have no trouble reading my mac formated files on my Ubuntu. In fact on my external hard drive I reformated to to mac hfs+ to be sure everything be read by both. In synapic go through the cross platform sections. You will probably find some other apps that are useful.

Thanks. It's good to know that someone else has this setup and it works. Have you tried writing to the hfs+ disk from Ubuntu? Has that worked well for you?

---

### Post by cyberdork33 on 2008-12-31
You just have to disable journaling on the partition in order to allow writing from Linux.That is a limitation built into the Linux driver for that filesystem.

You are right about UFS, at least the last time someone tried it. Apple's form of UFS is not a format that Linux understands (standard UFS works in Linux, but not OSX).

---

