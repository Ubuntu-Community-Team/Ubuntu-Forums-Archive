---
title: "Loadlin win98 SE parameters problems"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-17
Hi

I feel I am almost there, but have one (at least!) outstanding issue.
My win98SE PC does not have a working CD drive so I have been working through the 'Loadlin' process. [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)


I have created a directory called c:\linux on the PC. Into it I have place loadlin.exe (extracted from loadlin.exe.gz), a file called 'linux' and a file called initrd.gz following the instructions on distribution specific notes (I can't remember which mirror I used but I found the files in ubuntu/dists/hoary/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)

I unpacked the initrd.gz file then ran
loadlin linux initrd=boot.bin

after a restart into MSDOS.

I got a message which said 'can't read initrd (or similar)' I haven't got the win98 PC available at the mo.

Any clues?

TIA

---

### Post by ubername on 2007-02-17
> **ubername said:**
> Hi

I feel I am almost there, but have one (at least!) outstanding issue.
My win98SE PC does not have a working CD drive so I have been working through the 'Loadlin' process. [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)


I have created a directory called c:\linux on the PC. Into it I have place loadlin.exe (extracted from loadlin.exe.gz), a file called 'linux' and a file called initrd.gz following the instructions on distribution specific notes (I can't remember which mirror I used but I found the files in ubuntu/dists/hoary/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)

I unpacked the initrd.gz file then ran
loadlin linux initrd=boot.bin

after a restart into MSDOS.

I got a message which said 'can't read initrd (or similar)' I haven't got the win98 PC available at the mo.

Any clues?

TIA

Actaul message was ''can't open image file for initrd''

Hope that helps.
TIA

---

### Post by ubername on 2007-02-18
> **ubername said:**
> Actaul message was ''can't open image file for initrd''

Hope that helps.
TIA

Shameless attempt to move post up board, so viewed by more people.

Has anyone succesfully used Loadlin from win98? Are my experiences odd?

TIA

---

