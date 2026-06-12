---
title: "BSD media?"
date: 2006-11-21
forum: BSD
---

### Post by Sunnz on 2006-11-21
Just wondering...

How is media support on BSD?

For the average x86 installation of FreeBSD, can you get win32codecs and install say mplayer?

What about Flash? Java?

---

### Post by slimdog360 on 2006-11-22
They havent ported the flash 9 beta over yet (last time I saw anyway) but other then that its about the same. To install somethings like openoffice is a pain but PCBSD makes all that a lot easier.

---

### Post by Sunnz on 2006-11-24
How is OOo a pain? Do you have to compile it yourself? (Or would "port" download and compiles it for you?)

Can you at least install Flash 7 then? Also, would Flash 9 be ported to BSD anytime soon?

How are win32codec supported? The same win32codec dll files just like in Linux? Or gstream or something?

Last but not least, is the support of file systems as extensive as Linux? (FAT/NTFS, ext2/3, reiser, xfs, hfs/+, samba, NFS, etc)

I know it is probably too much questions... sorry about that, and thanks for your replies!!!

---

### Post by slimdog360 on 2006-11-25
I cant answer all of them exactly but I'll try.

 I found that when trying to install openoffice I was forced into installing some java sdk with a few other things. It was almost an impossibility for me, but Im sure if I was to really sit down and read all about it, it woudn't be too hard. A lot of things you can install with a single command but there are still some dependency issues.

Yep there is a port for flash 7

Not to sure about the win32 codecs but Im sure there would be a port for those also. You can still use gstreamer and all those sorts of things.

Im sure freebsd, but I cant remember exactly, supports heaps of different file systems but it uses its own filesystem for the root, home etc partitions.

There is one thing about freebsd that I found to be almost unbeatable, the documentation. The freebsd handbook covers everything you need to know about it and its all in the one place. Needless to say I was always very impressed by it.
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/")

---

### Post by Sunnz on 2006-11-25
Oh ok thanks!!!

I'll look at the handbook too!

---

### Post by Sunnz on 2006-11-28
Is it possible to run 32-bit apps on 64-bit BSB like on Linux? (Via multilib??)

---

