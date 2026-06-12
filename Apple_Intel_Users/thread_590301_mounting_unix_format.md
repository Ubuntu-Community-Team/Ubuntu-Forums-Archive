---
title: "mounting unix format"
date: 2007-10-24
forum: Apple Intel Users
---

### Post by Monsoonx27 on 2007-10-24
So I have been having problems writting on my 500gb drive formated as ext3 in OSX. So I transfered me files to another external and formated the 500gb as unix file systent in osx and now i cannot mount it in gutsy.


Any ideas? Can ubuntu read unix files system formated drives?

The error I get is 
 
Unable to mount the volume.
mount: wrong fs type. bad option, bad superblock on /dev/sdc3, missing codepage or helper program, or other error. In some cases useful into is found in syslog - try  dmesg | tail or so

---

### Post by cyberdork33 on 2007-10-24
> **Monsoonx27 said:**
> So I have been having problems writting on my 500gb drive formated as ext3 in OSX. So I transfered me files to another external and formated the 500gb as unix file systent in osx and now i cannot mount it in gutsy.


Any ideas? Can ubuntu read unix files system formated drives?

The error I get is 
 
Unable to mount the volume.
mount: wrong fs type. bad option, bad superblock on /dev/sdc3, missing codepage or helper program, or other error. In some cases useful into is found in syslog - try  dmesg | tail or so
Depends on what filesystem 'unix' is to OSX... you have to have support in the kernel for whatever filesystem you want to mount.

---

### Post by Monsoonx27 on 2007-10-24
It is formated by OSX as the UNIX File System, I used disk utility to format it.
The partition type is Apple_UFS

I formated it using Mac OSX on the premise that ubuntu would support it because ubuntu is generally awesome


I found this but how can their not be a solution.
[http://ubuntuforums.org/showthread.php?t=500080&highlight=apple+ufs](http://ubuntuforums.org/showthread.php?t=500080&highlight=apple+ufs)
[http://ubuntuforums.org/showthread.php?t=500080&highlight=apple+ufs]("http://ubuntuforums.org/showthread.php?t=500080&highlight=apple+ufs")

---

### Post by cyberdork33 on 2007-10-24
I think this pretty much sums it up:
> Just as a side note: despite UFS being "UNIX", Linux actually doesn't support it very well at all.  When sharing data, you're better off using HFS+

There is apparently no Apple_UFS module for linux.

---

### Post by eldepeche on 2007-10-25
I would recommend formatting a partition to be shared between OS X and any Linux OS as HFS+. Linux has excellent support for HFS+, as long as you make sure journalling is turned off.

In addition, there doesn't seem to be any single such thing as the Unix File System. cf [Wikipedia](http://en.wikipedia.org/wiki/Unix_File_System#Implementations).

---

### Post by cyberdork33 on 2007-10-25
> **eldepeche said:**
> In addition, there doesn't seem to be any single such thing as the Unix File System. cf [Wikipedia]("http://en.wikipedia.org/wiki/Unix_File_System#Implementations").

Exactly. And from what I have read, Apple's Unix filesystem doesn't work well in FreeBSD either.

---

