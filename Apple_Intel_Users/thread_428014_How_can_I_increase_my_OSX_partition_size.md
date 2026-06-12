---
title: "How can I increase my OSX partition size?"
date: 2007-04-29
forum: Apple Intel Users
---

### Post by thenetduck on 2007-04-29
I have installed Ubuntu with refit on my MacBook and would like to make my OSX partition bigger and my linux partition smaller. Does anyone know how I can do this? Thank you, 

 The Net Duck

---

### Post by SergioA on 2007-04-30
As far as I know (but maybe some expert will help you better!), the only "non destructive" solution for the Mac OSX partition side, is to use iPartition from a bootable CD (or from a second Mac connected through firewire).

I've tried Gnome Partition Editor live CD ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) but it seems that it has still some problems dealing with the Mac partition (and it marks it with a yellow exclamation mark...)

Maybe you will have to use GPE to shrink the Linux partitions, then iPartition to enlarge the Mac one...

Ciao for now!

Sergio

---

### Post by ronocdh on 2007-04-30
> **SergioA said:**
> As far as I know (but maybe some expert will help you better!), the only "non destructive" solution for the Mac OSX partition side, is to use iPartition from a bootable CD (or from a second Mac connected through firewire).

I've tried Gnome Partition Editor live CD ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) but it seems that it has still some problems dealing with the Mac partition (and it marks it with a yellow exclamation mark...)

Maybe you will have to use GPE to shrink the Linux partitions, then iPartition to enlarge the Mac one...

Ciao for now!

Sergio
I have had similar experiences with GParted pushing around OS X partitions. I think what I did is shrunk my other parts with GParted, then used the OS X installer disc and ran the disk utility on it to finagle my main partition into being larger.

Please someone post if you've had pleasant experiences using GParted on HFS+.

---

### Post by thenetduck on 2007-05-06
I looked it up on gparted's website and they don't support HFS+ however I am going to try to shrink my Ubuntu partition with GParted and then use iPartition to increase the size of the HFS+ . Ill post once I get it to work or make a how to. 


 The Net Duck

---

