---
title: "Noob Dual Boot Feisty and Tiger"
date: 2007-10-02
forum: Apple PPC Users
---

### Post by driven1 on 2007-10-02
I just installed Feisty in a dual boot with Tiger on a tiBook 867. So far, everything works except sound, but I'm not too worried about that yet. I am having fun exploring with the world of Linux. The main issue I have is being able to mount the Mac OS X partition of my hard drive while working in Feisty. My firewire external and my video iPod won't mount either. They all give the same error message : 

hal-storage-fixed-mount-all-options refused uid 1000

My flash drive mounts up with no problem. Any ideas on how to fix this? Thanks

---

### Post by AlphaMack on 2007-10-03
Create a folder in /mnt to represent your mount point.  Then in your fstab:

```
/dev/hdaX /mnt/nameofyourfolder hfsplus defaults 0 0
```

where X is a number corresponding to your partition (e.g. /dev/hda5) and 'nameofyourfolder' is the name of your partition.  Once you edit your fstab, enable the partition.  You can use any of a handful of tools to do this, such as gparted.

---

### Post by driven1 on 2007-10-05
Thanks to your help, I got the internal Mac drive to mount once I figured out the text editor in bash :)

I haven't had time to try it on the external drives. I also need to do some searching to learn how to change the permissions so I can actually access my files now that I can see the folders. One stepm at a time...

---

### Post by AlphaMack on 2007-10-05
Ah yes, the catch.

If your OS X partition is journaled, you can't write to it.  Moreover, the UIDs assigned by Linux and OS X are different.

If you absolutely need to access your folders on the OS X side, you need a script to invoke  Nautilus as root.

---

### Post by grazie on 2007-10-06
If you want to share a lot of data between OS X and Linux I'd suggest creating a separate data partition with the HFS+ filesystem and journaling disabled. I'd also suggestion setting your Linux user account UID to match the OS X user account. Probably best to create a new user account on Linux. Alternatively you could make the filesystem on the shared data partition Ext2 and install the OS X kernel patch at [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/). However I've had lots of kernel panics with this on Tiger, hence I don't trust it and no longer use it.

I wouldn't recommend launching Nautilus or any other filesystem browser as root - certainly shouldn't be done on a regular basis. The consequences coud be fatal.

---

### Post by driven1 on 2007-10-06
Thanks for the tips. I suppose in the end, I don't really need to transfer a lot of files. For now, I can keep them on a external drive. I like the idea of making a non-journaled hfs partition. That could serve my purposes very well.

---

