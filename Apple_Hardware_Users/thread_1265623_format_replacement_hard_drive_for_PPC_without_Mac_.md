---
title: "format replacement hard drive for PPC without Mac tools?"
date: 2009-09-13
forum: Apple Hardware Users
---

### Post by sweetleaf on 2009-09-13
Hello,

I'm running Jaunty on an iMac G3 (PowerPC). I'd like to replace the hard drive. As I understand it, PPC startup drives must have proper Apple boot partitions (which precede yaboot in the startup process). However, there is no MacOS on the drive, and I have no MacOS discs, so I do not have access to the standard Apple formatting tools (Drive Setup / Disk Utility).

Do you have any advice about how to proceed? Is there a better forum for this question? 

One idea would be to clone the data from the current, working drive. However, the tools I've looked at do not look promising. PartImage requires a drive with partitions already initialized to the proper filesystems (I think?), and might not work on a big-endian computer anyway. Clonezilla looks like a better option, and it supports HFS+, but the main page specifies "Intel-based Mac OS," which might be a bad sign.

I'd appreciate any suggestions you might have. Thanks!

---

### Post by zerobotman on 2009-09-13
i appologise in advance about my nubby answer but i've used some linux program called gparted for that kind of thing (albiet for an ibm intel based pc). maybe there's a plugin for it?

---

### Post by sweetleaf on 2009-09-25
Thanks, zerobotman. 

I found a [thread]("http://ubuntuforums.org/showthread.php?t=89960") in the archived forums where people have described using gparted to resize HFS+ partitions on their PPC machines. So we can confirm that gparted is compatible!

I'm still not sure about how best to set up the initial partition table and filesystems, though, or how best to make the data transfer. I'd love to hear from anyone who might have done this operation before, starting from an unformatted disk and using gparted (with dd? or tar??) to make it bootable on PPC hardware. 

Cheers!

---

### Post by gwydionwaters on 2009-09-25
if you use gparted? (i think that's it, the one in the installer) and set up the partitions it will automatically put in the mac part. i found this out un-educatedly deleting the mac table during install, i had to start over with no saved data in the end but it did add the table for me.

---

### Post by oswaldkelso on 2009-09-26
see:
[http://www.ppclinux.co.uk/wiki/maclin](http://www.ppclinux.co.uk/wiki/maclin) look at the open firmware and yaboot sections.

you can use any debian, ubuntu, disk to partition but could use the dd command to clone if you can mount both drives

be aware of the 8gb disk limit on 1st partition

---

