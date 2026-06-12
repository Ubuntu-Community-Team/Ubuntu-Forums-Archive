---
title: "howto change grub into its intalled partitation instead of MBR ?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by matiz on 2007-12-21
help!
howto change grub into its intalled partitation instead of MBR?

the XP is in /sda1
swap is in /sda7
ubuntu is in /sda8

grub is currently stored in MBR, and now I want store the grub in /sda8, how to make it?

---

### Post by Mud.Knee.Havoc on 2007-12-21
I find that the easiest way to play around with grub is to download the [Super Grub Disc]("http://freshmeat.net/projects/supergrub/").  It does everything!

---

### Post by matiz on 2007-12-22
Oh, just tested that super grub cd, well, it seems just a partition booting selector, I'm confusing which option will make my grub turn from MBR to it own installed partition ?!

---

### Post by meierfra on 2007-12-22
To install grub to the ubuntu partition, open a terminal (Applications->Accessories->Terminal) and type

```
sudo grub
root (hd0,7)
setup (hd0,7)
quit
```

But this does not erase Grub from the MBR. To  get rid of  Grub in the MBR you will have to install a different bootloader to the MBR (otherwise you won't be able to boot). You will also have to add ubuntu to  the menu of the new bootloader. What bootloader are you planning to use?

---

### Post by matiz on 2007-12-22
Hi, by following the above command, I got the next message:

----------------------------
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,7)     
root (hd0,7)
grub> setup (hd0,7)
setup (hd0,7)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0,7)"...  20 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0,7) (hd0,7)1+20 p (hd0,7)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 6: Mismatched or corrupt version of stage1/stage2

--------------------

sorry, I don't understand what it means ! :(

---

### Post by meierfra on 2007-12-22
I never have seen this error before. From the grub manual:

> 6 : Mismatched or corrupt version of stage1/stage2
           This error is returned if the install command points to incompatible or corrupt
           versions of the stage1 or stage2. It can’t detect corruption in general, but this
           is a sanity check on the version numbers, which should be correct.



Type

```
 sudo grub-install /dev/sda8
```
This will replace the stage files with the stage files in /usr/lib/grub/i386-pc and then install grub to sda8.

---

### Post by meierfra on 2007-12-22
If that did not work:


```
sudo apt-get purge grub
sudo apt-get update
sudo apt-get install grub
sudo grub-install /dev/sda8

```

If this did not work either:

```
sudo apt-get purge grub
sudo apt-get clean
sudo apt-get update
sudo apt-get install grub
sudo grub-install /dev/sda8

```

---

### Post by StGeorge on 2007-12-22
I wish I could help.
Grub is a pain.
I have lost access to my Ubuntu OS due to a power failure while does some tasks with partitrion magic.
I have now restored my 2nd HD to a state where it can be seen with its partitions with TestDisk.
I have now decided to use PQ Boot which comes with Partition Magic as my Boot Loader.
Can I get it to Boot Ubuntu. NO.
But I see I may have to follow above advice to nove Grub from MBR and put it into Ubuntu ex3.
Anyone with any other ideas.

---

