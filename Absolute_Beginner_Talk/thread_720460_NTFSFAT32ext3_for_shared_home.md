---
title: "NTFS/FAT32/ext3 for shared /home"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Lumby on 2008-03-10
I just bought a new computer with a 300gb HD. I plan on dual booting with XP and Ubuntu. Currently I plan on having:

50GB NTFS - XP partition
50GB ext3 - Ubuntu partion
2GB SWAP partition

With the remaining 198GB I was considering putting my /home on an NTFS partition so that it can be accessed by both ubuntu and xp, however I am not sure of the capabilities of the NTFS-g3 or if there are better options out there.

Any help or suggestions that can be offered would be greatly appreciated.

---

### Post by taurus on 2008-03-10
You cannot use ntfs filesystem for /home.  Doing so will cause you to not be able to log in.  If you need to share a partition between Ubuntu and windows, format it to ntfs and mount it to someplace like /media/share.  Furthermore, XP can read and write to ext2/ext3 just fine with fs-driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ShodanjoDM on 2008-03-10
Although the ntfs3g works wonderfully but it still can fails so I would suggest you to not putting your home directory on an NTFS partition.

IMO it's far better to create another Ext-3 partition for your home folder, so you can upgrade or even changing to another distro with much more ease.

---

### Post by Lumby on 2008-03-10
> **taurus said:**
> You cannot use ntfs filesystem for /home.  Doing so will cause you to not be able to log in.  If you need to share a partition between Ubuntu and windows, format it to ntfs and mount it to someplace like /media/share.  Furthermore, XP can read and write to ext2/ext3 just fine with fs-driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

So would you recommend having a separate partition for /home using ext3 then using the fs-driver to access it from XP? Also, could XP install and run a program on an ext3 file system using the fs-driver?

---

### Post by taurus on 2008-03-10
Yes, it's a good idea to have a separate /home with ext3 filesystem so that if you decide to reinstall, you can still keep all your personal settings in /home.  However, you cannot run Linux programs on ext3 filesystem with fs-driver.  The driver will only allow you to view and modify files on ext2/ext3, not running them.

---

### Post by forrestcupp on 2008-03-10
> **taurus said:**
>   If you need to share a partition between Ubuntu and windows, format it to ntfs and mount it to someplace like /media/share.  Furthermore, XP can read and write to ext2/ext3 just fine with fs-driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

When I tried that, it supported ext2 well, but was a pain to work with ext3.  Maybe it's changed now, though.

But I do the first thing taurus said.  I just put the files I need to share on my Windows NTFS drive.  It's easier that way because NTFS support in Linux is a little better than ext3 support in Windows.

---

### Post by Oldsoldier2003 on 2008-03-10
> **forrestcupp said:**
> When I tried that, it supported ext2 well, but was a pain to work with ext3.  Maybe it's changed now, though.

But I do the first thing taurus said. ** I just put the files I need to share on my Windows NTFS drive.**  It's easier that way because NTFS support in Linux is a little better than ext3 support in Windows.
thats the most sensible solution IMO

---

### Post by ShodanjoDM on 2008-03-10
One word of caution when using Ext2 IFS from Windows to access Linux partition:

You can easily delete or modify the "protected" folders so limit yourself to access only your home folder.

---

### Post by Arkenzor on 2008-03-10
It's paranoia actually, but I also hate the idea of my unsafe and crashy Windows being able to access all my Linux partitions. I'd stick to NTFS for a shared partition, it's not such a bad filesystem either.

---

### Post by Oldsoldier2003 on 2008-03-10
> **Arkenzor said:**
> It's paranoia actually, but I also hate the idea of my unsafe and crashy Windows being able to access all my Linux partitions. I'd stick to NTFS for a shared partition, it's not such a bad filesystem either.

yeah i just dont trust the stabilty of windows enough to trust writing to ext2/3 partitions from winders...

---

### Post by Duck2006 on 2008-03-10
> **Oldsoldier2003 said:**
> yeah i just dont trust the stabilty of windows enough to trust writing to ext2/3 partitions from winders...

+1

---

### Post by forrestcupp on 2008-03-10
Just remember, **do not** make your /home partition NTFS.  Just use your Windows NTFS partition for the files you need to share.  I actually have my Windows Documents, Downloads, and Music folders as custom 'Places' in the left side of Nautilus, so it's easy to get to those files.

---

### Post by louieb on 2008-03-10
> **forrestcupp said:**
> When I tried that, it supported ext2 well, but was a pain to work with ext3.  Maybe it's changed now, though.

But I do the first thing taurus said.  I just put the files I need to share on my Windows NTFS drive.  It's easier that way because NTFS support in Linux is a little better than ext3 support in Windows.

> **Oldsoldier2003 said:**
> thats the most sensible solution IMO

I'll go ahead and make it 3 thumbs up.

---

