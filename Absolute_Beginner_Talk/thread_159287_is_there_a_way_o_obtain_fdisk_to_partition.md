---
title: "is there a way o obtain fdisk to partition"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-04-12
i'm trying to partition my friend's computer but he does not have fdisk on his windows machine.  Is there a way to obtain fdisk so i can do this partition?

---

### Post by jazzmuzik on 2006-04-12
I'm not recommending this -- I've never done it -- but I wonder if those boot disks online would have fdisk... You could seriously get a virus, corporate or gov't piggybacking this way, but Google this:

"windows boot disk OR disc fdisk" (without the quotes)

Consider yourself warned.

---

### Post by davebgimp on 2006-04-12
I've had very strong success using this CD.
[http://www.sysresccd.org/](http://www.sysresccd.org/)

I use it every time I set up a dual-boot and/or just create a partition.

---

### Post by racermike1967 on 2006-04-12
is there a way to install fdisk.exe into ms-dos.  I downloaded fdisk.exe but i need to put it in ms-dos.  How do i do this?  Double clicking it doesn't do the job.

---

### Post by jazzmuzik on 2006-04-12
I'm pretty sure you want to boot up via a Windows floppy and run fdisk.exe from there, not by booting up into a dos/windows session and then running fdisk.exe from there. You can put fdisk.exe on a separate floppy or on your boot floppy (or cd-rom). Then set your computer's bios to boot up via the floppy (or cd-rom). After bootup you should be able to access fdisk. 

My memory is not 100%, but the point I'm alluding to above is I don't even think Windows/DOS will let you run fdisk except by a floppy boot up. I could be wrong about that, but I've always done it from a floppy boot disk.

And FWIW, the Ubuntu installation process gives you the option of partitioning your disk if you are installing Linux. I can't remember if it gave an option to set up fat and fat32 partitions.

---

### Post by zorlab on 2006-04-13
[QUOTE=jazzmuzik]I'm pretty sure you want to boot up via a Windows floppy and run fdisk.exe from there, not by booting up into a dos/windows session and then running fdisk.exe from there. You can put fdisk.exe on a separate floppy or on your boot floppy (or cd-rom). Then set your computer's bios to boot up via the floppy (or cd-rom). After bootup you should be able to access fdisk. 

My memory is not 100%, but the point I'm alluding to above is I don't even think Windows/DOS will let you run fdisk except by a floppy boot up. I could be wrong about that, but I've always done it from a floppy boot disk.

And FWIW, the Ubuntu installation process gives you the option of partitioning your disk if you are installing Linux. I can't remember if it gave an option to set up fat and fat32 partitions.[/QUOTE]


Thatis correct Jazz  - I might add sometimes getting a good img or imz (image) file can ge tricky, at times, at least getting a viable copy to floppy :o 

here is  a great choice of tools for this and other utils via floppy :

[http://www.answersthatwork.com/Downright_pages/downrights_bootdisks.htm](http://www.answersthatwork.com/Downright_pages/downrights_bootdisks.htm)

A thirty day trial should dothe trick  8)

---

### Post by jazzmuzik on 2006-04-13
BTW, if you find a windows boot disk -- like from a friend -- and want to make a copy of it the Linux way (assuming you are sure the disk is virus free), do this. Put the windows floppy boot disk in drive a and run this

dd if=/dev/floppy of=Windows98BootDisc.iso

Now you have a copy of the floppy on your hard drive. You can write it back to floppy like this. Insert a blank floppy and :

dd if=Windows98BootDisc.iso of=/dev/floppy

---

