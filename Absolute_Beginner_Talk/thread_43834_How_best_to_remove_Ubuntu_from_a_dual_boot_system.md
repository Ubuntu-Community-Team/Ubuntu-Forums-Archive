---
title: "How best to remove Ubuntu from a dual boot system"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by FireFusion on 2005-06-23
I installed Ubuntu on my dad's laptop just to test it on a high spec system, anyway he is going to want it back to normal without any of his Windows partition harmed.

I've had bad experiences uninstalling Linux in the past (boot loader problems to be exact). 

Could someone give me a step by step on how to uninstall?

Btw, I accepted the default location for the boot loader.

---

### Post by TravisNewman on 2005-06-23
Grab a System Rescue CD: [http://www.sysresccd.org/]("http://www.sysresccd.org/")
Burn the image you get

boot it up, type in the prompt "run_qtparted"
There you can delete the Linux partitions and make the windows partition grow.

You CAN resize the partitions with the Ubuntu Install CD or Live CD, but all they have is parted, which I still need a pen and paper to figure out what I'm doing with parted. qtparted gives it a nice interface. That System Rescue CD will come in handy later down the road though, I promise ;)

boot up a windows boot disk, or just boot into windows, and type, in a command prompt, "fdisk /mbr"

Should be exactly as it was.

---

