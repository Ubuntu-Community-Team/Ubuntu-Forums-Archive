---
title: "(Almost) good news for shared filesystems between OSX and Linux"
date: 2008-12-17
forum: Apple Hardware Users
---

### Post by cyberdork33 on 2008-12-17
[http://apple.slashdot.org/article.pl?sid=08%2F12%2F17%2F167220&from=rss]("http://apple.slashdot.org/article.pl?sid=08%2F12%2F17%2F167220&from=rss")

I believe, now, with AncientFS, you can create and use a non-Apple UFS partition in both Ubuntu and OSX...

---

### Post by _mario_ on 2008-12-17
> **cyberdork33 said:**
> 
I believe, now, with AncientFS, you can create and use a non-Apple UFS partition in both Ubuntu and OSX...
i think it's quite interesting and worth reading, but the author states at the [provided link]("http://osxbook.com/software/ancientfs/"):
[INDENT][I]AncientFS is an open-source MacFUSE file system that will mount ancient Unix data containers in read-only mode, making their contents available as regular volumes on Mac OS X. Examples of "data containers" include file system disk images, tape images, incremental file system dumps, tape archives, and library archives. Once mounted, you can browse the volume in the Finder, of course, but the true flavor of ancient Unix data can only be had through the command line.
[/I][/INDENT]
i really like him (the command line rocks) :p i'd like to use it on Linux.

however, it doesn't seem to be a solution for effectively and reliably sharing files between OSX and Linux ;-)

ciao,
Mario

---

### Post by stream303 on 2008-12-18
Well this blows my mind!

I just installed the latest security update 2008-008 on my G5 ppc iMac, and guess what?  The system now recognizes my internal drive formatted as ext3 with an openSuse installation, and doesn't seem to throw up any errors!

With disk utility, my Linux partitions now show up as Apple_Unix_SVR2

I can read everything on the disk, and even write to the ext3 partition from within osx 4.11 now.

Wonders never cease!

---

### Post by beauman on 2008-12-18
> **stream303 said:**
> 

I just installed the latest security update 2008-008 on my G5 ppc iMac, and guess what?  The system now recognizes my internal drive formatted as ext3 with an openSuse installation, and doesn't seem to throw up any errors!

With disk utility, my Linux partitions now show up as Apple_Unix_SVR2

I can read everything on the disk, and even write to the ext3 partition from within osx 4.11 now.



I updated my OS X today as well (version 10.5.6.) but I can't see any difference. On the desktop for example I only have the "Macintosh HD" icon. ExtFS still reporting errors when activating the ext2 partition.

---

### Post by Chrisj303 on 2008-12-18
> **beauman said:**
>  I only have the "Macintosh HD" icon. ExtFS still reporting errors when activating the ext2 partition.

Strange.

What type of Mac is this?

I have Ubuntu 8.10 running on an Ext2 partition, and ExtFS mounts, reads and writes to it perfectly - and has for a while..
Its just Ext3 that it doesn't like.

---

### Post by beauman on 2008-12-18
MacBook4-1

---

### Post by Chrisj303 on 2008-12-18
Same here (2.5ghz/Penryn - the one in my sig got stolen).

*Oh hang on, I'm on a Macbook Pro! - but I can't imagine that making any difference.

---

### Post by beauman on 2008-12-18
I think the Ext2Fs driver is out-dated. It is in fact strange that it works for you. Maybe it this one partition bit that Mac OS needs to see "external" partitions. No idea. But I don't care that much about Ext2Fs.

I think what stream303 reported was more interesting, that ext3 worked out of the box with his native Mac software and hope he provides some more details.

---

### Post by cyberdork33 on 2008-12-19
> **_mario_ said:**
> however, it doesn't seem to be a solution for effectively and reliably sharing files between OSX and Linux ;-)

darn. Well, I am still keeping my fingers crossed for ZFS. I just wish the licensing would get changed so that it can be added into Linux.

---

### Post by cyberdork33 on 2008-12-19
> **beauman said:**
> I think the Ext2Fs driver is out-dated. It is in fact strange that it works for you. Maybe it this one partition bit that Mac OS needs to see "external" partitions. No idea. But I don't care that much about Ext2Fs.
he is using ext2 not ext3 which is a big compromise IMO.

> **beauman said:**
> I think what stream303 reported was more interesting, that ext3 worked out of the box with his native Mac software and hope he provides some more details.

The big difference might be PPC. Still interesting. Maybe someone forgot to remove some developer code... I think I will download the update from Apple and see if I can't explore it a bit.

UPDATE:
It appears that there are updates to smbfs and AFP filesystems. I don'e really see anything that would have to do with ext2/3 or Linux. Also, that code "Apple_Unix_SVR2" seems to only be on PPC systems from a quick google.

Something of interest though, there was an update of X11 in this package and and I had an idea. Wouldn't the Apple-distributed version of X11 include the keyboard layouts / mapping to handle all their keyboards properly? Do you think we might be able to replace xorg layouts with layouts from inside OSX to get better keyboard support?

---

### Post by flaggh on 2009-01-15
> **cyberdork33 said:**
> darn. Well, I am still keeping my fingers crossed for ZFS. I just wish the licensing would get changed so that it can be added into Linux.

Have you looked into Nexenta yet?  Sounds enticing, the stability of the OpenSolaris kernel and ZFS support combined with the user experience of Ubuntu.  I realize hardware support may not be as good since its running an OpenSolaris kernel, but if Snow Leopard comes out with ZFS support, it may be worthwhile to make the jump.

[Nexenta Home Page]("http://www.nexenta.org/os")

---

### Post by cyberdork33 on 2009-01-15
> **flaggh said:**
> Have you looked into Nexenta yet?  Sounds enticing, the stability of the OpenSolaris kernel and ZFS support combined with the user experience of Ubuntu.  I realize hardware support may not be as good since its running an OpenSolaris kernel, but if Snow Leopard comes out with ZFS support, it may be worthwhile to make the jump.

[Nexenta Home Page]("http://www.nexenta.org/os")

ZFS binaries for OSX are here:
[http://zfs.macosforge.org/trac/wiki](http://zfs.macosforge.org/trac/wiki)

---

### Post by flaggh on 2009-01-16
> **cyberdork33 said:**
> ZFS binaries for OSX are here:
[http://zfs.macosforge.org/trac/wiki](http://zfs.macosforge.org/trac/wiki)

Yep.  Pretty cool.  Still a little buggy though.  Leopard already does read only, right?  If that's the case, the next logical step would be to add write.

---

