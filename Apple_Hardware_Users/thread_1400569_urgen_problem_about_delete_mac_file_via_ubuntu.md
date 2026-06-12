---
title: "urgen problem about delete mac file via ubuntu"
date: 2010-02-07
forum: Apple Hardware Users
---

### Post by idsos00 on 2010-02-07
recently, i modified a file in macintosh hd>Library>system...
that cause the finder can't start, so i can't replace the file in the os

so, i use ubuntu livecd to boot up, hope that can delted the wrong file, 
but there still have problems!!

1 I use terminal from OSX install disk to turn off the journal
like that..
```
diskutil disableJournal "/Volumes/Macintosh HD"
```
that's seem fine
2 I found that the system files didn't have the permission limiting, but when i drag a file to there, a alert box said "read-only system"

how can i do??

I just have one computer, and i search and trial a night, but still not okay

can some one can help me:KS

---

### Post by linuxopjemac on 2010-02-08
can't you fix it from the terminal in the OSX CD ? Accessing files from Ubuntu to OSX is very difficult, if not impossible

---

### Post by idsos00 on 2010-02-08
> **linuxopjemac said:**
> can't you fix it from the terminal in the OSX CD ? Accessing files from Ubuntu to OSX is very difficult, if not impossible
how can do that..

i think my Macintosh HD>System>Library>PrivateFramework>coreUI>Version>A>SArtfiles.bin was gone wrong

it's possible to copy the new one through the mac osx disk
i don't want to re-install@@:o

---

### Post by linuxopjemac on 2010-02-08
just try, I don't know

---

### Post by idsos00 on 2010-02-08
> **linuxopjemac said:**
> just try, I don't know
Any command recommend?

---

### Post by linuxopjemac on 2010-02-08
I haven't played with OSX for so long that I don't remember, so I ask you:

is it possible to boot into OSX live environment from the CD ? So you have access to the Terminal program ?

Another option is to boot from the OSX CD and to go to Disk Utility. Maybe it can repair a broken OSX partition.

---

### Post by Tycho59 on 2010-02-08
> **linuxopjemac said:**
> I haven't played with OSX for so long that I don't remember, so I ask you:

is it possible to boot into OSX live environment from the CD ? So you have access to the Terminal program ?

Another option is to boot from the OSX CD and to go to Disk Utility. Maybe it can repair a broken OSX partition.

I agree, boot from the Mac OS X discs that came with the computer and run disk utility, and then have disk utility run disk repair.  What disk repair will do is verify all the permissions on the Mac OS X partition and fix all of the permissions that seem out of place.  It sounds like the folder in which you're trying to fix inadvertently obtained a bad permission somewhere.

---

### Post by idsos00 on 2010-02-09
> **Tycho59 said:**
> I agree, boot from the Mac OS X discs that came with the computer and run disk utility, and then have disk utility run disk repair.  What disk repair will do is verify all the permissions on the Mac OS X partition and fix all of the permissions that seem out of place.  It sounds like the folder in which you're trying to fix inadvertently obtained a bad permission somewhere.
actually, no use
they can't find the problem until checking, maybe there have a file to let it think pass

also, it's not relative to premission
is  the read-only SYSTEM problem, can't write on it

anyway, thanks your reply

---

### Post by oswaldkelso on 2010-02-09
[http://ubuntuforums.org/showthread.php?t=807890&](http://ubuntuforums.org/showthread.php?t=807890&)

I've always turned off journalling via OSX. But it can be done from Gnu/Linux. From memory you do need to set user ID also search the archive as I think the info's there.

clues here.
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=553628&](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=553628&)

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=657225&](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=657225&)

---

