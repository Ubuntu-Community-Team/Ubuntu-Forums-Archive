---
title: "Getting ext2fsx to work with Linux USB drive on OSX"
date: 2009-02-08
forum: Apple Hardware Users
---

### Post by rjmusto on 2009-02-08
Hi there.

I have a USB drive that has been used with Ubuntu on a laptop, now no longer with us and have been trying to get an OSX (Tiger) machine to mount the drive so I can move stuff off it.

I have installed ext2fsx on the Mac and it seems to be working ok. It mounts the drive from the GUI.

However, when displaying the contents of the drive with Finder, it does initially list the folders - but with no icons for some reason - but if I try to select a folder to open, it just disappears. This happens with all the folders - so I can't drill down or copy anything.

I have also tried mounting the drive from a Terminal window and get the same behaviour.

Any clues how to fix it?

Thanks.

---

### Post by cyberdork33 on 2009-02-09
get virtualbox for OSX:
[www.virtualbox.org](www.virtualbox.org)

install Ubuntu as a guest OS.

attach external drive to guest OS.

Copy files to wherever (network share is probably easiest here).

Reformat external to a format that you can use.

---

### Post by rjmusto on 2009-02-09
Cricky - never heard of Virtualbox. 

Will give it a whirl.  Many thanks for that.

---

### Post by cyberdork33 on 2009-02-09
> **rjmusto said:**
> Cricky - never heard of Virtualbox. 

Will give it a whirl.  Many thanks for that.
you could also use a trial of parallels or vmware fusion, but virtualbox is open source and free.

---

### Post by deanv on 2009-09-21
Cyberdork...above you wrote "attach external drive to guest OS".  Any more detailed directions you might offer would be much appreciated.  I have an ext3 USB drive, and I have installed virtualbox, but I cannot get the drive mounted with my linux guest.

-dvh

---

