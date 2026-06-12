---
title: "Hard Partition issues"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Cirdan Alcarin on 2007-03-12
Hello, I am a total noob when it comes to Linux, with that said please bare with me.  Ok I installed Ubuntu I used the partition software that came with the live cd, all I did was just make my second Hard drive (which I use for mainly keeping music and videos files on) small, and then using the space left over created my Linux partition; with the intention of still being able to see that NTSF partition in windows.  When I boot into windows, I cant see my second Hard Drive, but when I boot into ubuntu its on the desktop, any one know how to solve this puzzle? thanks for ya time.

---

### Post by tallman9 on 2007-03-12
try this driver and if ubuntu partition is ext3 one, then you'll be able to see it also from windows.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by dstew on 2007-03-12
On an Ubuntu terminal, enter

fdisk -l

and post the results.

---

### Post by Cirdan Alcarin on 2007-03-12
> **dstew said:**
> On an Ubuntu terminal, enter

fdisk -l

and post the results.

when I type that in all I get is nothing just takes me back to the command prompt. 

cirdan@cirdan-desktop:~$ fdisk -l
cirdan@cirdan-desktop:~$ 

am I typing it in wrong?

---

### Post by AtrejuT on 2007-03-12
you have to do
sudo fdisk -l

---

### Post by Cirdan Alcarin on 2007-03-12
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       17999   144576936   82  Linux swap / Solaris
/dev/hdb2           18000       24792    54564772+  83  Linux

thanks mate, I hope this info is helpful.

---

### Post by AtrejuT on 2007-03-12
as someone above already assumed your filesystem on the second hard drive (hdb, that is) is not anything windows can read natively.

If it indeed is ext3 you should follow the hint above to use the driver at
[http://www.fs-driver.org/](http://www.fs-driver.org/)

this is a windows driver, so you have to install it in windows in order to be able to see your harddrive.

good luck

atreju

---

### Post by Cirdan Alcarin on 2007-03-12
alright thanks I'll give it a shot, but just asking does this mean my second HD is entirely ext3?

---

### Post by Cirdan Alcarin on 2007-03-12
Thanks guys, its working like a champ! cant thank ya enough!

---

### Post by dstew on 2007-03-13
Only the hdb2 partition is ext3. The linux swap partition is not this type. It really doesn't have a file system on it, with directories etc.

---

