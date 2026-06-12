---
title: "Install Ubuntu in place of windows"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Alron1 on 2006-03-08
I have "aquired" a Compaq Deskpro (Pent. P3 1Gb Proc. with 40Gb HD) At the moment it has Windows on board which I want to completely remove and have work totally with Ubuntu. Is this possible? Can I "format" the HD and segment with Ubuthu? Any other "tips" NOTE: I am not an expert so be kind    :)

Due to a problem (computer will not start with 40 GB drive....) have replaced the hard drive with a 10 GB drive which has win. xp pro on board.

Will NOT start up from CD.......

---

### Post by Brunellus on 2006-03-08
if you have nothing on the windows partition that you want to save, then you can just install Ubuntu.  You will be given the option of dual-booting, or simply using the whole hard disk as a single ubuntu partition.  Do the latter, and you will be all-ubuntu, all the time.

---

### Post by lipatden on 2006-03-08
Alron

You can downloan the Ubuntu Live CD first, and boot it. This will give you a quick compatibility test to see if the system functions properly with Ubuntu alone. If you want to keep the Windows partition, use the GParted program to resize the existing partition and make space for your Linux installation.

Otherwise, just go ahead and clean the hard disk.

---

### Post by manicka on 2006-03-08
Yes, you can do that. Just boot from the install CD and follow the prompts.

---

### Post by az on 2006-03-08
Just pick the option to use the entire disk instead of resizing the existing partition to make room for ubuntu - that option will allow you to dual boot.  If there is enough space on the disk, that will be the default.

Since that is not what you want to do, pick the option that formats the whole disk.

---

### Post by Alron1 on 2006-03-11
I have replaced the Hard Drive with a 10Gb drive (has XP PRO installed) - cannot get computer to accept the 40Gb; don't know how to sort it out in the BIOS.

I put the UBUNTU CD in (note that I downloaded and burnt CD with version 5.1) but no go.... the computer starts up with windows xp. Checked BIOS for start up sequence: 1: CD; 2: A drive; 3. Hard drive, so it should start up with CD (have even swopped CD players - just in case)

Any suggestions PLEEEEEEEEEEeeeeeeeeeze???

---

### Post by stanz on 2006-03-11
Hi All,
hey Alron1, while in your box, the "Parallel ATA", cable you connected to the new 10g hd,
you can- i think- connect the end 'Master' connect, to the cd player,
And connect at the mid section - 'slave' to the hd.
Must check bios after, to make sure all is well & 'boot from cdrom' is first.
Is floppy working? Is that in bootup sequence? It can be removed "for this install time", or moved
down the list.
I hope this was help!
reply & let us know!!

---

### Post by stanz on 2006-03-11
Ha, sorry folks...but i just remembered...
that would entail checking/changing the pin connect, on the HD itself,
where it configs- "Master" and "Slave". Sometimes located inbetween the 
Parallel ATA & Power= plugins. A lil` diagram might be scratched in-nearby.
It's all pretty simple, with tweezers or if your into getting your fingers dirty ;)

---

