---
title: "How to Make a partition"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-22
Hi i've got 100 gigs free, and i want to make a partition of 60 gigs ( i plan to put windows in there)  How can i make a new partition?

---

### Post by erfahren on 2008-01-22
[Gparted](http://gparted.sourceforge.net/) LiveCD works well

one note - is case you didn't know - Windows needs to be on a primary partition - this page has good info as well: [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

---

### Post by CheShA on 2008-01-22
Use System > Administration > Partition Editor  which I think comes installed by default if not then 

```
sudo apt-get install gparted
```

will install it.

---

### Post by CheShA on 2008-01-22
dang!! ;)

I'll have to make up for my lateness by adding another hint - Installing Windows *after* Ubuntu will overwrite the Grub bootloader on your your MBR and so you wont be able to boot Ubuntu, Just straight into Windoze.  Check [this thread ]("http://ubuntuforums.org/showthread.php?t=224351")for how to get it back.

---

### Post by wolfen69 on 2008-01-22
put in live cd.
open terminal.
```
sudo su
```
```
gparted
```
```
umount /dev/sdxx
``` (xx being the drive you want to resize)
choose resize.
choose unpartitioned space.
choose to make new partition. (the rest is self explanatory)
click apply.
done.

---

### Post by agim on 2008-01-23
How do I find out the name of a drive for the command umount /dev/sdxx?

---

### Post by zabien1970 on 2008-01-23
I believe when you run the live cd you can go to System>Administration>GnomePARTitionEDitor (gparted) and use the gui interface

---

