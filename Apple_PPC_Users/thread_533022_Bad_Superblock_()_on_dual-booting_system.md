---
title: "Bad Superblock (?) on dual-booting system"
date: 2007-08-23
forum: Apple PPC Users
---

### Post by clararaubertas on 2007-08-23
Hey,

I'm dual-booting Ubuntu and OSX on my iBook G4. Recently, it stopped being able to boot into Ubuntu with a "couldn't mount filesystem" message; it boots into OSX fine.
My problem is, I'm unable to figure out how to diagnose/repair filesystem issues from within OSX; I'm not even familiar with what my partitions are called here! :( I have OSX partition (seems to be fine), Ubuntu partition (seems to need some repair), and partition for files shared between the systems (seems to be fine).

So I am not even sure if /dev/disk0 is the Ubuntu partition, but it was the only plausible-looking thing in /dev and results below seem to indicate that it may be?

FROM WITHIN OS X,
```
sudo fsck /dev/disk0
``` gives:
```
BAD SUPER BLOCK: MAGIC NUMBER WRONG

LOOK FOR ALTERNATE SUPERBLOCKS? [yn] y

SEARCH FOR ALTERNATE SUPER-BLOCK FAILED. YOU MUST USE THE
-b OPTION TO FSCK TO SPECIFY THE LOCATION OF AN ALTERNATE
SUPER-BLOCK TO SUPPLY NEEDED INFORMATION; SEE fsck(8).
```

```
sudo newfs -N /dev/disk0
``` lists some blocks, including block 32; but ```
sudo fsck -b 32 /dev/disk0
``` (and with some of the other numbers) gives:
```
Alternate super block location: 32
** /dev/rdisk0 (NO WRITE)
BAD SUPER BLOCK: MAGIC NUMBER WRONG
```

Any suggestions are greatly appreciated!!

---

### Post by stmiller on 2007-08-23
You'll have to boot the Ubuntu PowerPC Alternative CD and type 'rescue' at the boot prompt to enter rescue mode. From there you can get to a terminal and fsck to repair the disk. I'm not sure if OS X can properly read and repair ext3 partition info.

---

### Post by frog_pilot on 2007-08-23
do what stmiller said and type at the prompt

```
sudo fsck.ex3 -p /dev/hdaX
``` for X you have to type the number of your root-partition ... maybe 3 for the third partition of your harddisk...

the option -p is for automatic repair without any questions

If you don't know exactly the number of the partition you could start from the edgy-desktop cd. on my ibookG4 800MHz it works fine. I think Feisty-desktop-cd won't work, because of problems with the updated ATI-Driver. You have to start gparted and there you will find the correct identification.  Then you can open a terminal and and type the stated code...

---

### Post by clararaubertas on 2007-08-23
Thanks, I will try this!

---

### Post by frog_pilot on 2007-08-24
Sorry, I forgot a letter in the code! :oops:

You don't have to type > **frog_pilot said:**
> sudo fsck.[COLOR="Red"]ex3[/COLOR] -p /dev/hdaX

The right syntax is:```
sudo fsck.[COLOR="Red"]ext3[/COLOR] -p /dev/hdaX
```

Hope, you will read this before trying... :-?

kind regards

---

