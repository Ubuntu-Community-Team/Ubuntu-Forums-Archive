---
title: "Reading a windows burned dvd on ubuntu"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by plumberchris on 2008-02-03
Before switching from vista to ubuntu i burned all of my files to dvd using the windows burning program, before switching i double checked to make sure the dvd's were readable( i have had windows screw that up before) and as far as i could tell they were closed out right and readable. Although after deleting vista and installing ubuntu i tried to recover my files from the dvd's and ubuntu would not even recognize the dvd. Any thoughts on this would be greatly appreciated, I have work files on these dvd's and kinda need to get to them.

The Error i keep getting is 
Cannot mount volume.
invalid mount option when attempting to mount volume "udf Volume"

---

### Post by philinux on 2008-02-03
I'd try them on a windows machine too.

---

### Post by SunnyRabbiera on 2008-02-03
did you finalize the disc?

---

### Post by plumberchris on 2008-02-03
Disc was finalized and they did work on a microsoft machine just not on the ubuntu

---

### Post by plumberchris on 2008-02-03
I had also burned the ubuntu system to dvd the same way and that dvd is readable....

---

### Post by philinux on 2008-02-03
There is a workaround in here ...

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233)

---

### Post by rustutzman on 2008-02-03
It looks as though you used the udf or drag to disk to burn them. You will probably need to find another computer with the same udf software installed. Most often only the software that was used to burn them will read them.

If you had burned them using the burning software interface instead of udf they'd more than likely show up fine.

Russ

---

### Post by plumberchris on 2008-02-04
ok so this is the error i get when trying to mount dvd in terminal

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is after i changed fstab

---

### Post by mc4man on 2008-02-05
as Russ said the file system vista uses by default for burning data disks isn't generally readable in linux - may depend on which of the 4 udf types you used
basic info
[http://windowshelp.microsoft.com/Windows/en-US/help/2af64e60-60aa-4d79-ab6c-3a5db5806cbe1033.mspx](http://windowshelp.microsoft.com/Windows/en-US/help/2af64e60-60aa-4d79-ab6c-3a5db5806cbe1033.mspx)

---

