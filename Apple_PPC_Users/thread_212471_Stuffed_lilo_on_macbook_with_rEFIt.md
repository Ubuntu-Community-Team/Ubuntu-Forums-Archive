---
title: "Stuffed lilo on macbook with rEFIt"
date: 2006-07-09
forum: Apple PPC Users
---

### Post by sglynnsp on 2006-07-09
Hi,

I installed ubuntu on my macbook as per instructions in [http://bin-false.org/?p=17]("http://bin-false.org/?p=17")

however I made an error when updating the kernel. I ran 
```
lilo 
```
instead of
```
lilo -b /dev/sda
```

and it wrote boot information (don't know the term) to sda3 (which is my ext3 / partition), so that when I reboot and rEFIt pops up the options I have three options (boot OSX from HD, Boot Linux from HD, boot Linux from sda3) instead of two (boot OSX from HD, Boot Linux from HD). 

I tried to undo my error with the command
```
lilo -u /dev/sda3
```

however it seems only partially successful, because although rEFIt doesn't show the linux tux icon on option 3 any more, it still has an option 3 (i.e. boot from sda3). It seems to think sda3 is still bootable, just doesn't know what's on it.

Does anyone know how to fix this?

Cheers
Simon

---

