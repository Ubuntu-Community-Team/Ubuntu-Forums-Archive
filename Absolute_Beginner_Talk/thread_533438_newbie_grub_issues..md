---
title: "newbie grub issues."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by wickstopher on 2007-08-23
Hello, there.  I was hoping someone could either answer my question outright or point me towards the right documentation.  After a little searching, I can't really come across exactly what I need.

After dual-booting Ubuntu and Windows for some time, I decided to fool around with some other distributions of Linux.  First off, I installed Edubuntu, because I'm planning on buying a new computer at some point in the future and passing this machine on to my 3-year-old for learning/entertainment.  I messed around a bit, but decided it wasn't worth configuring it quite yet, so I installed Zenwalk on the same partition, as I've heard a lot of good things about Slackware being a great platform for learning more about how Linux works.  I allocated a partition using the Gparted LiveCD, and installed Zenwalk.  The first time through, I was prompted as to whether or not I wanted to install LILO, and decided no, because I figured I was more than happy with the way GRUB was working.  Big mistake.  Apparently, when I installed Edubuntu, the configuration for GRUB was stored on that partition, and when I overwrote that partition, my GRUB settings went with it.  I was getting a bootloader error and couldn't boot into any of my operating systems.  So, I tried again, reinstalled Zenwalk, this time choosing the LILO option.  This worked for accessing my Windows and Zenwalk partitions, but for some reason it wasn't seeing my Ubuntu partition.  I tried a couple of things that I can't remember, tried configuring LILO, but gave up.  I ended up installing Linux Mint Cassandra on the partition, and that put a GRUB loader back on my machine and enabled me to boot into my beloved Feisty partition.

Now, here's my question.  I want to keep experimenting with that third partition, but I don't want to deal with the bootloader problem again.  How do I default the GRUB settings to my main Ubuntu partition, and how do I avoid overwriting the bootloader with new distro installations on my third partition?

It's probably clear from my wording that I'm not entirely sure of how the bootloader works or how it's installed.  Any help would be greatly appreciated!

[wickstopher]

---

### Post by pxwpxw on 2007-08-24
Get, or make, a grub cd or floppy. That will let you boot anything manually.

Don't install any bootloader when trying other stuff - keep the ubuntu grub as master. 

Then you can manually edit the ubuntu grub /boot/grub/menu.lst to boot any additional systems. 

Of course it will need a bit of reading about grub, but shuold cover all contingencies.

---

