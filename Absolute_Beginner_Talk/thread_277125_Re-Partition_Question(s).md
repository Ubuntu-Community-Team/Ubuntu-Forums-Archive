---
title: "Re-Partition Question(s)"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Will5639 on 2006-10-14
Running dual-boot pretty nicely, at first I only assigned 20 gig's to Ubuntu (19 root, 1 swap) .. and already am looking to make tweaks to sizes.

Outta a 100gig drive, currently:

20 Gig Volume (primary) - Windows (NTFS) (C:\)
53 Gig Volume (logical) - Windows (NTFS) (D:\)
19 Gig Volume (logical) - Linux (ext3)   (\)
1 Gig Volume (logical?) - Swap

-

I know linux reads fat32 (320gig external) .. so I'd imagine a regular partition formatted as fat32 on the harddisk would be understood too, right?

So would it be possible, if I free'd up some space on C and D.. to make a partition of Fat32, that *here's my goal* is readable via both windows and ubuntu?

So I could put items like music / movies / pictures in there instead of having duplicate copies?  As well as use it like a transport drive when I want to shift files from linux -> windows // windows -> linux?

----------

If so far I've got your attention with a *yes thats possible* answer... how should I go about doing it?

Get on Windows and Partiton Magic, freeing up the space from there?  Then creating the partition from windows?  Or should I get something to resize partitions from the linux side, and then create the fat32 partition from linux?

I don't wanna corrupt and have to install windows / my whole computer all over again.

---

### Post by Kateikyoushi on 2006-10-14
Did you consider using extfs windows drivers ? [Link]("http://www.fs-driver.org/"). Then you could read and write your linux partition from windows.

Might save you from going through this process.

---

### Post by jorn on 2006-10-14
Be aware of movies on a fat32 filesysstem.The max. filesize is 4GB.

---

