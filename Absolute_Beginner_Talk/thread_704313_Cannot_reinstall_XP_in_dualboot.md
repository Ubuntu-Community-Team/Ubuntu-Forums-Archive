---
title: "Cannot reinstall XP in dualboot"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by vishnu_sresht on 2008-02-22
I had installed gutsy along with  Xp ... both OSes worked perfectly for sometime ... now my XP has crashed .. I inserted the XP installation disk and attempted to install a fresh copy of Xp. I formatted my old XP partition (originally partition1). I then created a new partition 

(partition 5, with Ubuntu and swap being partitions 2 and 3; and partition 4 being my NTFS common data drive that i use for storing songs and stuff). 

After XP  finishes copying files onto the new partition, it asks for a reboot. After the reboot NOTHING happens! My grub has been killed (I restored it using Ubuntu live CD) and it just won't boot into  my XP partition in order to complete the setup! Is this because XP is now being installed in the latter part of my hard drive? Please help me get my dual-Oses back.

---

### Post by neurostu on 2008-02-22
check your grub.conf file their should be a entry under the XP partition that says something like "chainloader +1" if there isn't try adding it. That could fix your problem

The problem is that windows has its own boot loader. Grub needs to be told to load the windows boot loader. If it doesn't then it cannot correctly start windows.

---

### Post by Joeb454 on 2008-02-22
You might find that Windows needs to be installed at the "front" of the hard drive, not the "end" I don't know why, but it just does.

This could be your problem

---

### Post by dstew on 2008-02-22
Windows needs to be in a primary partition (usually partition 1 to 4). It won't work from a logical partition, like 5. Ubuntu will work from a logical partition though.

---

### Post by piousp on 2008-02-22
I'm not sure, but i think both OS need a primary partition. :confused:

---

### Post by Hendrixski on 2008-02-22
I think  you just hosed your setup  :-(  The Windows install overwrites the boot loaders, and then craps all over the place.  You can recover your Ubuntu data with a liveCD, then you might have to re-install.

Windows doesn't play nicely with others, so you need to contain it in something like a virtual machine.  that way when it reaches its half-life and you have to re-install it you can just click the "revert" button and it sets it back to its original install.

Thus, my suggestion:  install just Ubuntu, then download VMWare Server, and install Windows on the VM....   Or just don't bother with it.  I had a dual boot but found that I wasn't using the windows partition anymore because, well, the software on it just wasn't as good.  So I wanted the space back and deleted Windows.  :-)

---

