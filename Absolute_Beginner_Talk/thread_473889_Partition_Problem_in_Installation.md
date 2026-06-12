---
title: "Partition Problem in Installation"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by tomkuang on 2007-06-14
I was stuck in step 4 of the installation: choose my partition. A program was loaded to check the partition and checked for ever (1 hour actually, that's my max limitation). I could do anything I want during the time (surf the net, email, play music,etc). It just not go to step 5. To give you an idea, my computer is:
Giga 694T Pro Mobo+Tulatin Celeron 1GHz+512Mb RAM+Ati AIW 7500+8139 Ethernet+80Gb Seagate ATA100
80Gb HD: 10Gb NTFS for XP system (active primary partition)
10Gb for Ubuntu (formatted or not, ex3 or NTFS, primary or logical, doesn't matter, same problem)
rest of the partiotions are in extended NTFS

Thanks again for your input!

---

### Post by Seisen on 2007-06-14
Its because you processor is slow, you should  have or try the alternate disk. That way you can do a text based install.

---

### Post by bren on 2007-06-14
perhaps there is a partition table problem which is preventing the partition editor from seeing your fs properly.   does your existing os boot ok?

but maybe seisen has it right it is just a slow processor and you need alternate cd.....

you could try running testdisk to check if you don't mind burning another iso.

you can get this on the gparted live cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 

let us know how you get on

bren

---

### Post by tomkuang on 2007-06-14
Thanks all for your input!
Benifit from the 512Mb RAM, I think my computer is actually faster than you think. I could boot from live CD and run all the program smoothly(better than XP). I'll take your suggestion to check the disk for errors first.

---

### Post by nzcyclone on 2007-06-17
Am getting a similar problem when trying to install. Ironically Windows Server installed and was working fine on the computer now trying to install Ubuntu it is having problems. System is a AMD Sempron 3000+ with 1GB RAM the hdd is on a card and is NOT off the motherboard. Ubuntu install does detect it as a SCSI device (sda) seem to be getting through the installation fine untill get to the partitioning section. I tell it to partition all the drive (want windows off it) it seems to start and then just hangs there, eventually it comes up with I/O error writing to device /dev/sba ;retry/ignore/cancel. all options just seem to loop back to same error. Any help greatly appreciated and thank you :) Will add though the hdd is NOT a SCSI but is a IDE hdd I am assuming it detected it as that because is off an additional card. I do have a linux driver for the card, is there a way to tell the installer to load it on install?

---

### Post by dptxp on 2007-06-17
I do not think that your processor is so slow that you need more than one hour to see your partition table.
It can be bad CD too.

---

### Post by candtalan on 2007-06-17
> **tomkuang said:**
> Thanks all for your input!
Benifit from the 512Mb RAM, I think my computer is actually faster than you think. I could boot from live CD and run all the program smoothly(better than XP). I'll take your suggestion to check the disk for errors first.

I do not think your PC is slow - I have something similar and it is the fastest machine in my house which is mostly full of PIII 500Mhz machines.....  :-)

Using the live CD in your PC and the CD start menu to check  the CD also checks the drive, although it takes a while to finish.

I have had better results on a few occasions with gparted (itself a live CD) than the ubuntu live CD installer partitioner.

Your HD - ensure you have defragged it (twice) before you begin, and do scandisk etc also,  and check there is enough space. I hear that windows sometimes has files on the drive which cannot be moved, and I wonder if this can sometimes give a problem for the partitioner. 

Extended NTFS - I do not know about this, maybe it is causing complications. Partitioning can lead to massive loss of data, Be sure to have a good backup first eh?

---

