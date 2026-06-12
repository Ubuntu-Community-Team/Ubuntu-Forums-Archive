---
title: "How to run Windows XP inside Ubuntu"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-05-30
Can somebody explain to me in detail how to run Windows XP inside Ubuntu.

---

### Post by Error1312 on 2007-05-30
See [this]("http://ubuntuforums.org/showthread.php?t=39513") thread.

Or you can use VMWare, but it isn't free.

---

### Post by superdexter on 2007-05-30
That's correct VMware (vmware.com) is not free.  But I can say that the new version 6 is amazing.  I've seen a performance increase over the 5.x series as well as native USB 2.0 support which means iTunes and my iPod no longer cause VMware to crash!  I highly recommend it, is it the single reason I'm allowed to run linux in my office since I can still produce Microsoft documents.

---

### Post by gn2 on 2007-05-30
> **superdexter said:**
> That's correct VMware (vmware.com) is not free.  

Here are the free VMWare options: [http://www.vmware.com/download/free.html](http://www.vmware.com/download/free.html)

Wouldn't bother with "Player" though.

Also Virtualbox is worth a try. [http://www.virtualbox.org/](http://www.virtualbox.org/)

VMWare Player, Server, and Virtualbox are all available through [www.getautomatix.com](www.getautomatix.com)

---

### Post by mijj on 2007-05-30
i installed vmware server ...

the vmware server console came up ok.

then i created some space for a virtual machine ok .. but ... i cant install xp into the created empty virtual machine.

When i power on ... i just get a blank screen that just sits there for a few moments then falls back to the vmserver console.  The cd rom drive lights flicker like it's looking for the cd in there.  But it doesnt do anything with the cd.

I also tried setting the vm cdrom to point at an iso image of teh xp install disk - same blank screen result.

Anyone care to make a suggestion?

---

### Post by mijj on 2007-05-30
... any kind of suggestion will do ...

*[SIZE="1"]<waits hopefully>[/SIZE]*

---

### Post by mijj on 2007-05-30
no suggestions then?

---

### Post by mijj on 2007-05-30
well .. in case anyone's interested ...

... i messed around and discovered ...

i created teh virtual machine on an ntfs partition via ntfs-3g.   The installation of the os into the virtual machine wouldnt work from there.   

I creeated a virtual machine in teh linux partiton and i *could* install the os into the virtual machine.

VMware loses one point against VirtualBox for not working with a virtual machine on an ntfs partition.

---

### Post by bsalt on 2007-11-24
Hey, is it possible to install the VMWare server, and just point it the Windows partition, and if so, how do I do it?

---

### Post by ronmarley1 on 2007-11-24
Sorry to deviate from what you are doing, but I did this just as an experiment with VirtualBox and it was very easy.
[http://www.virtualbox.org/](http://www.virtualbox.org/)  They even have a repo for Gutsy.
The only glitch I had was after I installed VirtualBox, I had to tell it to mount the CD ROM drive to see the Windows install disk (it was two or three clicks).  It did not do this by default.  Once I did that, the install of Windows was easy.

---

