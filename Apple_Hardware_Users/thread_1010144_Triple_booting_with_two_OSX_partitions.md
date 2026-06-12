---
title: "Triple booting with two OSX partitions"
date: 2008-12-13
forum: Apple Hardware Users
---

### Post by colinhayes on 2008-12-13
Does anybody know of a way to configure yaboot.conf so that I can have an option to boot into ubuntu, OSX 10.5, and OSX 10.4?  The man page makes it sound like I can only have one macosx= statement in there and that I can't just throw it into the macos= statement because that's meant to only boot an OS9 partition.

any help?

---

### Post by mkvnmtr on 2008-12-13
Yes, Tiresia wrot a good thread on this just a few day ago. I don't know how to post a link but search for PPC-Yaboot-How to configure the PPC bootloader- Multibooting. I tried to follow it but got involved in other nthings and haven't done it yet.

---

### Post by pxwpxw on 2008-12-13
> **colinhayes said:**
> Does anybody know of a way to configure yaboot.conf so that I can have an option to boot into ubuntu, OSX 10.5, and OSX 10.4?  The man page makes it sound like I can only have one macosx= statement in there and that I can't just throw it into the macos= statement because that's meant to only boot an OS9 partition.

any help?

The standard install of yaboot has only one macosx and one macos option.
I just tried it, you can use macosx for the first one, macos for the second giving the 'x' and 'm' option,
In yaboot.conf for example with only 1 macosx on /dev/sdb3
```

macosx=/dev/sdb3
macos=sd1:3 

```
Then run ybin to update the boot file ofboot.b
Both boot  macosx at that partiton, I checked the ofboot.b bootfile, looks ok
It boots sd1:3,\\:tbxi, same format as for macosx=sd1:3
Just needs your adress for the second macosx, which needs to be blessed (tbxi).
 
This is set by the small CHRP script ofboot.b which makes the l  'l x m c' menu and gets installed in the bootstrap partition along with yaboot.
It can also be hacked to have a second macosx option, but that requires an edit of ofboot.b
and would get overwritten when ybin runs.

Might be easier to just use the Option key if that works, also to check that both are blessed (I can,t do that here with only one macosx).

Post if you need more help with it.

---

