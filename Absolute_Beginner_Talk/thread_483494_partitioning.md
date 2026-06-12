---
title: "partitioning"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by octopuskevin on 2007-06-24
Hey there, I've been looking for an answer to this, but I just can't seem to find it!

What is the best way to create a separate partition for kubuntu and ubuntu? I want them each independently so that menu items and so forth don't get mashed together... essentially I just want to keep my gnome programs with gnome, and kde with kde.

should I be making a second /home partition, or a second / or something completely different? 

Any help would be awesome!

Thanks!!! 

- Kevin

oh and if wondering, my current drive setup is a /home, /, and swap... no windows.

---

### Post by alan_daniel on 2007-06-24
Do you have any unused space on your hard drive? And by unused, I mean unassigned, not just free space on your / or /home partitions.

If you do have unused space, you can simply install the second distro and create the / partition out of that, and tell it to point to the /home (but make sure it does NOT reformat it) for the /home stuff. So basically make new partitions for everything except the /home partition if you wanted to use the same /home for each distro.

If you don't have unused space, you can use a partition manager to resize whatever partition you can free up some space in. Once you have unassigned (unpartitioned) free space, then you can do the same thing I mentioned above.

Theoretically this process should work. I've never done it in practice, so I can't verify its success.

---

### Post by Happy_Man on 2007-06-24
Hmm... you do know you can edit the menus for each one, so that the programs from the other are not showing, right? It's what I do.....

But yeah, just resize your / partition, and install the other onto there. Point it to the existing /home BUT DON'T REFORMAT! Swap will be automatically picked up, no need to make a new one. This will be very confusing on bootup, however. GRUB will show two absolutely identical lists together... good luck finding which one is which.

---

### Post by alan_daniel on 2007-06-24
> **Happy_Man said:**
> GRUB will show two absolutely identical lists together... good luck finding which one is which.

Once you figure out which is which, though, you can edit the /boot/grub/menu.lst file and change the names of the entries so that you yourself can know which is which.

---

### Post by louieb on 2007-06-24
Sure you can. Setup is no different from dual booting Fedora and Ubuntu. see the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") for GRUB setup ideas. I use a configfile  to dual boot two Linux. Have used the chainloader option in the past it works well also. 

Probably not going to want to share the home partition. can be all kinds of problem with user config files and program locations.


There no right way to partition but there are ways that don't work. .

---

### Post by octopuskevin on 2007-06-24
sweet thanks for the replys guys

yeh i know i can edit the menu's, but i really want to keep as much as possible apart...

i've been using gnome for quite a while, and just want to make another easy partition for messing with strictly kde. 

appreciate the quick responses!

- Kevin

---

