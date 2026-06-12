---
title: "SSHFS won't work between mount points"
date: 2013-03-09
forum: Any Other OS
---

### Post by Fishbowler on 2013-03-09
Disclosure: I've already tried posting this question on the Linux Mint forums, but the folks there weren't able to help. Given the upstream dependency, I thought you kind people might be able to help.

I'm trying to remotely manage a filesystem from Mint 14 to Mint 12. There's a folder where everything gets dumped - logs from work, recent downloads, etc, etc, etc, and I periodically go through it and put everything in the right place. There are four data partitions that get mounted on boot. The "dumping ground" exists on one of them, but "the right place" might be on any one of them. I've recently discovered SSHFS, which seems like an ideal solution - I can use two panes in Nemo (the recent Nautilus fork) and move files around the remote file system.

The big problem: Moving files between the mount points on the remote filesystem gives "Operation not permitted" - any ideas?

Smaller problem: Copying files between the mount points (the workaround) copies them over the network via the other machine - is there a way for this operation to happen "remotely", as it would if I did it whilst ssh'd to the box?

Of course, if anyone has an alternative to SSHFS that beats remote desktop, I'm not precious!

Thanks up front for any time spent considering this, even if you end as stumped as me.


_Extra info_:

I used this as a reference: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

The partitions are DATA0, DATA1, DATA2, DATA3
The dumping ground is a folder in the root of /media/DATA3
I've tried moving to folders in the root of DATA1 and DATA2 - both give the error.

The exact command I ran was:
```
sshfs -o idmap=user dan@192.168.3.99://media/ ./remote
```

Whilst searching, I found this: [http://sourceforge.net/apps/mediawiki/fuse/index.php?title=SshfsFaq#mv_fails_with_.22Operation_not_permitted.22.](http://sourceforge.net/apps/mediawiki/fuse/index.php?title=SshfsFaq#mv_fails_with_.22Operation_not_permitted.22.)

So tried mounting like this: ```
sshfs -o idmap=user,workaround=rename dan@192.168.3.99://media/ ./remote
```
No change. I assume I've got the formatting of the options right (i.e. comma separated) but haven't found any specific reference...

---

### Post by The Cog on 2013-03-09
You could always just run nautilus on the remote server, with its display showing on your desktop:
```
ssh -X 1.2.3.4 nautilus
```

---

### Post by Fishbowler on 2013-03-09
Wow! That's so simple, elegant & perfect! Thanks a billion!

---

