---
title: "GnomeBaker, wodim and suid"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by haelters on 2007-03-18
I'm looking at [https://code.launchpad.net/baltix/+source/cdrkit/+bug/82082](https://code.launchpad.net/baltix/+source/cdrkit/+bug/82082), since I have the same problem. However, there is something I do not understand. Why does wodim have to be suid ? 
If I run wodim (without suid) from command line it works fine:
```

manfred@shire:~$ ls -l $(which wodim)
-rwxr-xr-x 1 root root 386496 2007-02-02 18:52 /usr/bin/wodim

manfred@shire:~$ wodim blank=fast
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
... (cut out for forums)
Starting to write CD/DVD at speed  10.0 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.

``` 

So now why does Gnomebaker does not work while wodim isn't suid ? Is there a hard coded check on suid in the source of Gnomebaker ?

Manfred

---

### Post by haelters on 2007-03-18
Well, I've just found out that cdrecord needs to run with suid due to it's internal workings  (see [https://bugs.launchpad.net/ubuntu/+source/gnomebaker/+bug/63539)](https://bugs.launchpad.net/ubuntu/+source/gnomebaker/+bug/63539)). However, I agree with Andriy Tymchenko that this isn't good practice. However, I'm still with some questions:
1/ is wodim the Debian fork of cdrecord ?
2/ ifso, isn't it possible that the requirement of suid is removed from there ? (even at a performance penalty)

Manfred

---

### Post by mrguytx on 2007-03-29
if I run "sudo gnomebaker" it will burn, so it's definitely a permissions issue....
hope it's fixed in final feisty.

G

---

