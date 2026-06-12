---
title: "Please help me mount my shiney new iPod!"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-12-25
When I double click it, this shows up.
[[IMG]http://img228.imageshack.us/img228/3316/screenshotnautilussy4.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshotnautilussy4.png)

Amarok doesn't detect it too. Does anyone have their iPod syncing with Amarok like iTunes?

(I have a 2nd gen Nano btw)

Thanks, and Merry X-Mas!

Edit
I installed gnome-mount, and now this is showing up.
[[IMG]http://img85.imageshack.us/img85/4435/screenshotnautilus1jf0.th.png[/IMG]](http://img85.imageshack.us/my.php?image=screenshotnautilus1jf0.png)

---

### Post by Azakus on 2006-12-25
That looks like the iPod has some corruption on the disk. Anyway try this:
```
sudo aptitude install hfsplus hfsutils gtkpod
```
Then try gtkpod to access your iPod.

---

### Post by Charco on 2006-12-31
Thanks, but I couldn't get it to run. It turns out that the new Nano acts differantly than other iPods.
This thread was incredibly helpful:
[http://www.ubuntuforums.org/showthread.php?t=316244&highlight=ipod+howto](http://www.ubuntuforums.org/showthread.php?t=316244&highlight=ipod+howto)

---

### Post by ichigo on 2007-01-13
I'm running Dapper and encounter the same error message, when clicking on the "Apple iPod Musik-Player" icon (which is shown under Places->Computer). Since [http://www.ubuntuforums.org/showthread.php?t=316244&highlight=ipod+howto]("http://www.ubuntuforums.org/showthread.php?t=316244&highlight=ipod+howto")  does only apply to Edgy, it's of no help to me. :-? 

As far as I've understood HAL is not able to read the iPod (a 2g nano with 8GB formatted for Windows,btw).

```
dmesg | tail -32
```
returns 
```

[17181843.948000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17181843.948000] FAT: bogus logical sector size 2
[17181843.948000] VFS: Can't find a valid FAT filesystem on dev sda.
[17181843.968000] FAT: bogus logical sector size 2
[17181843.968000] VFS: Can't find a valid FAT filesystem on dev sda.
[17181843.984000] NTFS-fs warning (device sda): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17181843.984000] NTFS-fs error (device sda): ntfs_fill_super(): Device has unsupported hardsect_size.
[17181844.000000] NTFS-fs error (device sda): ntfs_fill_super(): Device has unsupported hardsect_size.
[17181844.016000] HFS+-fs: unable to find HFS+ superblock
[17181844.036000] HFS+-fs: unable to find HFS+ superblock
[17181844.084000] VFS: Can't find ext3 filesystem on dev sda.
[17181844.104000] VFS: Can't find ext3 filesystem on dev sda.
[17181844.120000] VFS: Can't find an ext2 filesystem on dev sda.
[17181844.136000] VFS: Can't find an ext2 filesystem on dev sda.
[17181844.156000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17181844.172000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17181844.308000] XFS: bad magic number
[17181844.308000] XFS: SB validate failed
[17181844.324000] XFS: bad magic number
[17181844.324000] XFS: SB validate failed

```

Does anybody know how to fix this problem in Dapper? It shouldn't be a problem of the ipod, because the same messages occur, when connecting my mother's 2g 4GB.
Thanks in advance!

---

### Post by nitu14 on 2007-02-13
Hi, I have the same problem, I have installed all these packages from:

[http://gamesplace.info/opensource/ub...ipod-nano-fix/](http://gamesplace.info/opensource/ub...ipod-nano-fix/)

follow the instructions.

Now I can see the Ipod icon on my Desktop.


Thanks martin.

---

