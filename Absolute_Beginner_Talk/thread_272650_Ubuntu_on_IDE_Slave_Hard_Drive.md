---
title: "Ubuntu on IDE Slave Hard Drive"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by ubuntuross on 2006-10-06
Is it bad to have Ubuntu installed on the Slave hard drive in my computer?  I have WinXP on the primary drive and didn't want to have to reparition etc.  The system monitor shows that it is waiting on I/O an awful lot.  Could that be the reason why?

I am using an ASUS P4S8X-X motherboard.

Thanks.

ubuntuross

---

### Post by gn2 on 2006-10-06
I use PCLinuxOS this way, and it works fine, so Ubuntu should be OK too.

There's plenty people doing it without difficulty.

---

### Post by louieb on 2006-10-06
Two operating systems two hard drives? It has been my experience that I have less trouble if I give each operating system its own drive.

---

### Post by bodhi.zazen on 2006-10-06
> **ubuntuross said:**
> Is it bad to have Ubuntu installed on the Slave hard drive in my computer?  I have WinXP on the primary drive and didn't want to have to reparition etc.  The system monitor shows that it is waiting on I/O an awful lot.  Could that be the reason why?

I am using an ASUS P4S8X-X motherboard.

Thanks.

ubuntuross

This will work fine and I do not think is the cause of your I/O issue.

> **louieb said:**
> Two operating systems two hard drives? It has been my experience that I have less trouble if I give each operating system its own drive.

Two hard drives are no more or less trouble then one, unless you have to resize windows.

---

### Post by gn2 on 2006-10-06
> **bodhi.zazen said:**
> 
Two hard drives are no more or less trouble then one, unless you have to resize windows.

Don't forget two hard drives with Windows having un-grubby non-corrupted mbr, and Ubuntu on separate drive is significantly simpler if you ever want to remove or re-install either operating system. 

For example if your Windows suddenly fell ill with a very nasty virus infection? 

Saves having to muck about re-installing Grub and re-configuring it.

---

### Post by bodhi.zazen on 2006-10-07
> **gn2 said:**
> Don't forget two hard drives with Windows having un-grubby non-corrupted mbr, and Ubuntu on separate drive is significantly simpler if you ever want to remove or re-install either operating system. 

For example if your Windows suddenly fell ill with a very nasty virus infection? 

Saves having to muck about re-installing Grub and re-configuring it.

You have a point, but you scheme has it's own set of hassles.

If you set a GRUB floppy and a /boot partition for /grub/menu.lst and it is very easy to wipe/reinstall any OS on partition/ any drive any time. This only needs be done once and circumvents the MBR.

All I am saying is that with the exception of resizing windows, two drives are not more or less hassle then one.

For each problem there is at least two solutions, usually equal in hassle. Pick one and go with it.

---

### Post by gn2 on 2006-10-07
> **bodhi.zazen said:**
> You have a point, but you scheme has it's own set of hassles.

If you set a GRUB floppy and a /boot partition for /grub/menu.lst and it is very easy to wipe/reinstall any OS on partition/ any drive any time. This only needs be done once and circumvents the MBR.

All I am saying is that with the exception of resizing windows, two drives are not more or less hassle then one.

For each problem there is at least two solutions, usually equal in hassle. Pick one and go with it.

Floppy drive? Last seen boarding Noah's Ark!

HeeHee laughed the cheeky penguin....

---

### Post by bodhi.zazen on 2006-10-07
[list=number][*]LOL :lol:
[*]I may  be old, but not that old !
[*]The only new box I have seen without a floppy is a laptop. Not that I know much about all that new stuff mind you, I'm lucky to spell DVD.
[*]Besides, as if the name were not a clue, worng religion.[/list]

---

### Post by gn2 on 2006-10-09
> **bodhi.zazen said:**
> Besides, as if the name were not a clue, worng religion.[/list]

Does that mean it's possible you believe USB flash drives could be re-incarnations of old floppy drives no longer of this world?

HeeHee laughs the cheeky penguin....

---

