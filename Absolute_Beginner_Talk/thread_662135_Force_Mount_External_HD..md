---
title: "Force Mount External HD."
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Deeper on 2008-01-08
Hi People.

My External HDD is NTFS formatted. It gives an error message saying it failed to mount because NTFS is flagged as in use. It advises me to either go into windows or force mount.

I do not have any version of windows to use, so I must attempt to force mount it. How would I go about doing this?

I tried what it suggested but it just came back with the mount --help stuff.

The disk is called

"FreeAgent Drive"


Thank you VERY much,

Deeper.

---

### Post by Pevichaey5 on 2008-01-08
there are some issues that can crop up when using an NTFS partition with Linux.  Maybe you could change it to a FAT file system that way Linux, Windows, etc can read and write to the drive without any problem.

you will need to install FOS which will allow you to write to an NTFS partition but i haven't used one yet so i'm not entirely sure how successful that will be

hope that helps

---

### Post by Deeper on 2008-01-08
> **thexero said:**
> there are some issues that can crop up when using an NTFS partition with Linux.  Maybe you could change it to a FAT file system that way Linux, Windows, etc can read and write to the drive without any problem.

you will need to install FOS which will allow you to write to an NTFS partition but i haven't used one yet so i'm not entirely sure how successful that will be

hope that helps

I'm not bothered about changing the format, however I need to get the files from it first if at all possible.

---

### Post by Pevichaey5 on 2008-01-08
ok

i would advise you install FOS, Linux mounts the File System and then you can mount it like any normal device, then you should be able to drag and drop the files

in the unlikely event you don't have permission to do so, Alt + F2 >> sudo nautilus >> to get root powers so you should have permission to copy the files

sorry also see this link about it [ntfs mount](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by eRion on 2008-01-15
Hi,
I had the same problem before.
What you have to do is to check whether u have FUSE and  also check if you have NTFS-3g and NTFS-config. If you dont have them you will have to get them and install them. Then its pretty easy. Just plug the drive and run the program. 
I hope this will help.

---

