---
title: "[SOLVED] Grub 1.5 Error 25/17..."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by kvarley on 2008-02-19
Hello, 
        I recently installed Ubuntu on my second HD. I then changed the HD to be the first one. I booted into windows and formatted the Ubuntu drive, now I get error messages:
> 
GRUB Loading Stage1.5

GRUB loading please wait...
Error 17 [or 25]

I think it is to do with the system BIOS which wants to boot from the Ubuntu drive.

My setup goes like this.
1st drive: 200GB Maxtor which I formatted. 
2nd drive: 160GB Western Digital Drive with 2 partitions.
                 C:\ is my windows partition. [20GB] 
                 D:\ is my partition for my work. [140GB]

Please respond soon!

---

### Post by MasterJS on 2008-02-19
GRUB was probably installed to the drive containing Windows, as it was the first one. By formatting Ubuntu and changing the order, GRUB is looking for the menu.lst file which contains the list of operating systems and now it cannot find it.

---

### Post by philinux on 2008-02-19
Sounds like you removed grub. It needs to be reinstalled using the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by bumanie on 2008-02-19
You should read this sie [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
it is probably the most informative grub guide available on the internet. It explains how to fix grub issues such as yours.

---

### Post by kvarley on 2008-02-19
Thank you to all who posted, I sucessfully fixed my computer.

I re-installed windows on my partition which then put windows as the first operating system to boot not Ubuntu.

---

