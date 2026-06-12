---
title: "How to format my external hard drive for shared use"
date: 2007-01-03
forum: Apple PPC Users
---

### Post by maxmartin on 2007-01-03
Through a complicated set of circumstances, I now have a Macbook and an iBook G4. I'm running OSX on the Macbook, and when I get the faulty hard drive in the iBook replaced I'm going to use it as my Ubuntu machine. I just got a 250 GB external hard drive to hold my music and such, and I was wondering what the best choice is for formatting it if I want to be able to use its contents in OSX & in Ubuntu. Should I just format the whole thing with a Unix filesystem, or do multiple partitions with different filesystems, or...

---

### Post by maxmartin on 2007-01-04
Bump...come on, anybody?

---

### Post by raul_ on 2007-01-04
FAT can be read in both systems and windows :)

---

### Post by maxmartin on 2007-01-04
Okay, that does make things simpler...but I've been a Mac user all of my Linux (besides my still pretty beginner-level forays into Unix), so I've heard plenty of spooky bedtime stories about defragging and all of that kind of stuff...would it make things cleaner or simpler to use any other filesystem or to partition, or should I just keep the whole thing FAT?

---

### Post by raul_ on 2007-01-05
I assume you're a Mac "power user" so try and look for ext drivers for Mac. When u install those, then you can format your external disc to ext3 and use it in both systems too ;)

---

### Post by ssam on 2007-01-05
linux works fine with hfs+ (though it might be best to turn journalling off)

or there are ext3 drivers for mac os x [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

---

