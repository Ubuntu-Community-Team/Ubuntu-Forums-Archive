---
title: "using the /home partition."
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by lewisskinner on 2007-11-30
Hi there.  I'm running Vista on a AMD 5000+ with 2GB of RAM and a 500BD hard disk.  I have partitions my drive already, with 40GB for windows, a 4GB swap and a 300GB shared partition in fat32.  The rest, around 25GB, will be for Ubuntu.  Now, just to make it easier for my girlfriend, can I set up the /home partition on the fat32 drive so that files created by ubuntu and windows are placed on the same partition by default?

---

### Post by Sef on 2007-11-30
> Now, just to make it easier for my girlfriend, can I set up the /home partition on the fat32 drive so that files created by ubuntu and windows are placed on the same partition by default?

Yes, you can.   Do you have some empty space or not?

---

### Post by hyper_ch on 2007-11-30
Sef: Are you sure a fat32 disk can be mounted as /home?

---

### Post by tszanon on 2007-11-30
> **lewisskinner said:**
> Hi there.  I'm running Vista on a AMD 5000+ with 2GB of RAM and a 500BD hard disk.  I have partitions my drive already, with 40GB for windows, a 4GB swap and a 300GB shared partition in fat32.  The rest, around 25GB, will be for Ubuntu.  Now, just to make it easier for my girlfriend, can I set up the /home partition on the fat32 drive so that files created by ubuntu and windows are placed on the same partition by default?
Sure. When installing ubuntu, just select that partition and assign it to /home.
There are other ways to achieve the same result, but I think that this one will be the easiest to implement.

And by the way: 4GB swap is a lot more than you will ever need. I have 1 GB RAM and my swap partition has only 500MB. It's almost never used.

---

### Post by philinux on 2007-11-30
I think the only thing with fat32 is permissions. You need to set the permissions for the mount point .

---

### Post by lewisskinner on 2007-11-30
Yes, I just tried a dual-boot and lost a lot of my stuff, so I reinstalled windows and then partitioned.  All I have on the fat32 drive (mounted as e:) is a copy of the directory structure from c:/users that Vista creates (but no files).  If I set this drive as the /home, my hope is that is will create a folder for each user with /music, /documents, /videos etc inside, and then I can just direct the windows start menus to look in the e:/home/lewis/documents (or whatever) by editing the shortcut in the start menus.

Oh, and I know 4GB swap is massive, but with a 5GB HD, it's not as though space is at a premium :)

---

### Post by lewisskinner on 2007-11-30
Would I be better just creating/editing shortcuts on Ubuntu (is this possible?) telling it to look in the fat32 drive, and then just creating a small /home partitiion to keep my settings separate?

---

### Post by hyper_ch on 2007-11-30
lewisskinner: Shortcut are called "symbolic links"

```

sudo ln -s /path/to/where/the/shortcut/shall/point/to /path/to/where/the/shortcut/shall/reside

```

e.g.

```

sudo ln -s /media/hdb3 /home/lewisskinner/Desktop/Fat32

```

---

### Post by mmcmonster on 2007-11-30
A better option is to create the /home directory as ext3.  Then install in Windows [ext2 IFS]("http://www.fs-driver.org/").  It allows MSWindows to read and write ext2 and ext3 filesystems.

---

### Post by hyper_ch on 2007-11-30
hmmm, I'm not so sure about the ext2/3 drivers anymore... I'm sure they work fine but if your windows get hijacked wouldn't it then be possible to also erase your data on the ext3 partition as it would be rw-mounted?

---

### Post by philinux on 2007-11-30
bottom line is home is where ubuntu puts its config files for apps. Storing large multimedia files or documents can just about go anywhere.

---

### Post by tszanon on 2007-11-30
> **hyper_ch said:**
> hmmm, I'm not so sure about the ext2/3 drivers anymore... I'm sure they work fine but if your windows get hijacked wouldn't it then be possible to also erase your data on the ext3 partition as it would be rw-mounted?

Yes, it's possible. But it's just the same when using /home partition as fat32 and accessing it from windows.

---

### Post by lewisskinner on 2007-11-30
> **philinux said:**
> bottom line is home is where ubuntu puts its config files for apps. Storing large multimedia files or documents can just about go anywhere.

Oh yeah, I know.  But my girlfriend is an even less-advanced user than I am, so I just want Ubuntu to save on the fat32 drive by default so she knows where everything is

---

### Post by Paqman on 2007-11-30
These days a shared partition can even be NTFS. That'd be significantly better than FAT32 (bigger files, less fragmentation, etc) and both OSes can handle it by default.

---

### Post by atlfalcons866 on 2007-11-30
ntfs is also journaled and fat32 is not

---

### Post by lewisskinner on 2007-11-30
Are you sure Ubuntu can handle NTFS?

And what does "journaled" actually mean?  I keep hearing this mentioned

---

### Post by mmcmonster on 2007-11-30
Ubuntu 7.10 (Gutsy) comes with read-write support for NTFS by default.

That being said, it uses [NTFS-3g]("http://www.ntfs-3g.org/index.html") to do this, and I'm not sure if there will be any performance hit by using it as a /home partition.  According to [this table]("http://www.ntfs-3g.org/performance.html"), the performance doesn't seem too bad.

One thing: NTFS and FAT32 are case-retentive but not case sensitive.  You may run into issues if you use filenames with mixed case but otherwise identical names.  It's not really an issue except if you have digital cameras. (I have two digital cameras, one which uses IMG0000, while the other uses img0000.)

---

### Post by lewisskinner on 2007-12-02
OK, just tried that, and Ubuntu installation cannot label a NTFS drive as /home.  Is there any way I can do this afterwards, so that I can keep my setting in /home, and default my files to be saved in the shared NTFS partition within "/users/lewis"?

---

### Post by jken146 on 2007-12-02
If you can't set an NTFS partition to be /home, the next easiest thing to do would be to make it ext3 and install the Windows ext driver.

---

### Post by lewisskinner on 2007-12-02
Is there no simple way to just tell linux that when I click places -> documents, to look in "/home/users/lewis/documents", when I click places -> music, look in "/home/users/music"?

---

### Post by lewisskinner on 2007-12-02
> **mmcmonster said:**
> A better option is to create the /home directory as ext3.  Then install in Windows [ext2 IFS]("http://www.fs-driver.org/").  It allows MSWindows to read and write ext2 and ext3 filesystems.

tried this.  Didn't work

---

### Post by Paqman on 2007-12-02
What didn't work about it? Were you able to assign the partition a Windows drive letter?

---

### Post by lewisskinner on 2007-12-03
I didn't even try - Ubuntu couldn't even find it!

Seriously, I just want to click "places -> documents" and have Ubuntu open "/home/lewis/documents".  Is there no way I can reassign the shortcut?  Ubuntu is supposed to be super-customisable, but something which is as simple as a right-click and typing apparently cannot be done!  This is silly.!  Can't anyone tell me just how to redirect shortcuts to where I want?

---

### Post by philinux on 2007-12-03
Yes just put a launcher on the desktop pointing to that directory.

---

