---
title: "Formatting Hard Drive"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-23
I am looking to format a USB external hard drive that is currently formatted for the OS X file system, to  the EXT3 file system.I would like to have 2 partitions. Can someone tell me the best way to accomplish this?

---

### Post by the Didey on 2007-12-23
gnome partition editor.

gparted in synaptic or add/remove programs.

You can delete and move partitions.

---

### Post by fmbugdadi on 2007-12-23
with Gparted live CD, I can reformat the whole hard drive, and then create my partitions right?

---

### Post by L Campbell on 2007-12-23
> **fmbugdadi said:**
> I am looking to format a USB external hard drive that is currently formatted for the OS X file system, to  the EXT3 file system.I would like to have 2 partitions. Can someone tell me the best way to accomplish this?


From here ( [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) ) you can download a Live CD and it seems to work very well.

---

### Post by logos34 on 2007-12-23
> **L Campbell said:**
> From here ( [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) ) you can download a Live CD and it seems to work very well.

But you don't need to boot the live cd...like didey said you can just use the gparted that's installed.

fmbugdadi,
what's your fdisk show?

sudo fdisk -l

---

### Post by the Didey on 2007-12-23
yes, you can use gparted from the LIVECD or you can install it...both should work fine

go to synaptic and do a search, Systems---> Administration--->Synaptic Package Manager.:

---

### Post by fmbugdadi on 2007-12-23
Don't have the Hd in my possession yet, getting ready to pick it up. Just installed Gparted through synaptec.... So I will go pick up the drive, and post my results here..

---

### Post by fmbugdadi on 2007-12-24
Ok, guys, that worked for me,after the 2nd try. At first Gparted, for some reason, would not let me format the drive. I formatted with the EXT3 file system. I like this drive. It is a 160 gig external that takes its power from the USB. Now I know there is an option to use the this file system with Windows...

---

### Post by logos34 on 2007-12-24
> **fmbugdadi said:**
> I like this drive. It is a 160 gig external that takes its power from the USB. Now I know there is an option to use the this file system with Windows...

download this:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

yeah, bus-powered USB is nice.  (or bus-powered firewire-800, which is really really nice)

---

