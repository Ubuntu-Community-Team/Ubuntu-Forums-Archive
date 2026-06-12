---
title: "help asap please error 17"
date: 2010-01-08
forum: California Team - US
---

### Post by djbasicone on 2010-01-08
:(:(:(:(i only got this pc for a few more hours i got error 17 and my cdrom driver is not working only got flash drive on my note book and it shows no OS   >???? what to do ??????

---

### Post by arubislander on 2010-01-08
maybe this will help:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

Good luck...

---

### Post by manavendra on 2010-01-08
your problem might be because of some change in your partition table information. you can try booting into linux using a live CD and then doing:

```
fdisk -l
```choose option **x** (extra functionality (experts only)) and enter.
then select **f** (fix partition order) and enter.
then select option **w** (write table to disk and exit), and enter.
  Don’t do anything else unless you know what you are doing.

Once you have noted down your linux and swap partitions, you should verify that that grub menu.lst shows the correct boot information. 

```
vim /boot/grub/menu.lst
```Otherwise, you need to setup grub again providing the correct boot partition information. Assuming, your linux is installed in /dev/sda6, use[INDENT]```
$ sudo grub
 grub > root (hd0,5)
 grub > setup (hd0)
 grub > quit

```[/INDENT]

---

