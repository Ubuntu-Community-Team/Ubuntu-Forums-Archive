---
title: "Mounting a new disk"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by petr on 2005-09-02
So I have used Debian for the last few years and it sucks for all the reasons that ubuntu doesn't.

My question is about the Device Manager (System->Adimistration->Device Manager).  I know enough to know that devices are connected via the /dev/ part of the file system.  Very elegant idea; but how does a non-geek find out which /dev/xxxxx represents a thingy the Device Manager might find?  This is such an obvious thing to want to do, that I think I am missing something.

If you ask "what device am I trying to find?" I swear I will find out where you live and come around and punch you in the nose.  This is a generic question; for which there should be an obvious answer - surely!

Petr

---

### Post by Jussi Kukkonen on 2005-09-02
But of course there is :) 

Select a device in Device Manager, select Advanced tab, look at *block.device*

...ok, it wasn't obvious.


[edit: on second read it seems you wanted to do the search in the other direction... ]

---

### Post by dbcoder on 2005-09-02
sudo apt-get install gparted 

That will get you most storage devices shown.  It's a helpful utility :P

---

### Post by petr on 2005-09-05
[QUOTE=Jussi Kukkonen]But of course there is :) 

Select a device in Device Manager, select Advanced tab, look at *block.device*

...ok, it wasn't obvious.


[edit: on second read it seems you wanted to do the search in the other direction... ][/QUOTE]
 That sounded hopeful, but I thought I'd tried the Advanced option.  In fact I had; no block.device there I'm afraid.  I have noticed a discrepancy between my ubuntu 5.04 and the manuals... perhaps it has been fixed ...

petr

---

### Post by petr on 2005-09-05
[QUOTE=dbcoder]sudo apt-get install gparted 

That will get you most storage devices shown.  It's a helpful utility :P[/QUOTE]
 gparted looks good, but it doesn't help!  It only picks up the hard disk; I have a CD and a memory stick unmounted on the PCI bus.  Under Ubuntu, the Device Manager nicely lists everything - BIOS, Memory, Processor, IDE device (master), CXD3222 i.LINK COntroller, Memory Stick Controller ...  but /dev is full of other crap I know I don't want.  Which one is connected to the Memory Stick Controller?   I am sure the method of determining this is really a guild secret...

petr.

---

### Post by UbuWu on 2005-09-05
Breezy will have a disks manager which you can use for all disks.

---

### Post by ubuntme on 2005-09-05
No idea what you are after, but i'll have a go anyway.

Harddrives and CD/dvd drives look loo like hda, hdb, hdc, etc.  The partitions of a hard drive will look like hda1 and hda5 etc.

I have a hardrives hda and hdb for example, with partitions hda1, hda5, and hdb1 etc and DVD burner hdc.

USB drives turn up as sda, sdb etc.  my external drive is sda, with one partition sda1.

Hope that helps.

---

