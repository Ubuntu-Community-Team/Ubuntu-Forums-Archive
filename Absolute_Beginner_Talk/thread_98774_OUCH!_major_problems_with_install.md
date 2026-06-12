---
title: "OUCH! major problems with install"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by scratching my noggin on 2005-12-04
Hi everyone, Hoping someone can point me to some solutions, cause my hair is getting thin from the scratching!

Installing Ubuntu from CD onto Toshiba Satellite Laptop, followed the list of install actions, ie, select lan guage, keyboard, find and configure CD rom, etc. Came to the partition. I already had winXP installed, which I need for a while. I assumed like a redhat installation the partitioner would see the NTFS system. Went to manual, and set 18 Gig as the linux partition, and 700 Mbs for Swap. All went ok, completed the install and eagerly awaited the boot loader to ask me which system to boot into. 

Oh! it defaulted and booted to Ubuntu, with no time to go to Windows. Thats when I became suspicious, Cut to a day later.... the windows file system is wrecked. Partitioning overwrote or altered some critical sectors on the disk. 

Okay no great loss, as my data had been backed up, I thought just reinstall the windows system into the remaining partiton. NO way! it will not do it. 

OK, went on to Ubuntu to connect to the net and look for answers. Ubuntu cannot find the internal modem. I used PPPConfig from root, to configure the ppp stuff, but cannot find a dialer anywhere. By now I am almost bald. 

At this point I am reloading windows XP professional, from my second system, but will only be able to use this for a short while. 

Where can I get PRECISE step by step instructions, for accuratly shrinking down the 30 gig into two partitions, and making each of them ready to accept the two operating systems? 

Any ideas on the modem issue, and connectivity would also be greatly appreciated. I know deep in my heart (somewhere) that Ubuntu will work for me. 

Thanks people :-)

---

### Post by linbetwin on 2005-12-04
Format the hard drive with the Windows XP CD and then create two partitions (you choose the size). Install XP on one of the 2 partitions, then install Ubuntu on the other.

---

### Post by Kvark on 2005-12-04
Install XP, tell the installer to wipe the whole hard disk and then make 1 partition out of the space XP should have while leaving the space Ubuntu should have unpartitioned.

Then install Ubuntu and tell the installer to use only the free space.

---

### Post by scratching my noggin on 2005-12-04
[QUOTE=Kvark]Install XP, tell the installer to wipe the whole hard disk and then make 1 partition out of the space XP should have while leaving the space Ubuntu should have unpartitioned.

Then install Ubuntu and tell the installer to use only the free space.[/QUOTE]
Thanks guys, that looks easy. Any ideas on getting Ubuntu to see the modem? and how do I dial up when I get the whole thing set up again? 

Thanks for the help.

---

### Post by az on 2005-12-04
The XP installer cannot handle prepartitioned disks.  It cannot wipe the disk clean and start over.  You have to do that by hand with fdisk.  More often than not, you end up with a pretty screwy partition table if you let Windows try.

As for your original problem, I do not know why that happened.  Had you picked the default guided partitioning, the partitioner would have done all the work.  As it is, it may be that there was a human error or a hardware probelm involved.  Since people tend to complain about this sort of thing more than post messages about every successful mundane install, I would say this rarely happens.

What kind of modem do you have?  Hardware manufactureres do not share the specs or write open source drivers for software modems.  Most of the drivers for these things are closed-source precompiled drivers.  Some you have to actually pay for!

---

### Post by towsonu2003 on 2005-12-04
[QUOTE=scratching my noggin]Any ideas on getting Ubuntu to see the modem?[/QUOTE]

it's a pain in the *** to make modems work in linux if they are winmodems... these are modems that uses system cpu&ram instead of using their own hardware pieces (which do not exist, so they are cheaper) ...

for the starters, do the following (after fixing your installation issue :) ):
go to linmodems.org ; read the page ; download scanModem tool. 

after downloading scanModem to your linux system (preferably to ~/Desktop, which is your desktop, for easy access),
```

gunzip scanModem.gz 
chmod u+x scanModem 
./scanModem

```

Scanmodem will scan modems and tell you how to configure them. You will need to read 'read1st.txt' and 'modemdata.txt' under (I think) the folder 'Modem'. If you cannot understand what these are saying, modemdata.txt should have some important instructions (at the top) on how to email linmodems.org people...

good luck...

---

### Post by jimrz on 2005-12-04
OOOPs...try using PartionMagic from XP. I assume you do not already have this program. If you don't have a way to get one free, v8.0 is avilable at atomicpark.com for about $40 (incl shipping). It's agreat utility and should fix your problem pdq. If you do buy it, get the PowerQuest version which is identical to the Symantec (who bought out Powerquest) and about 1/2 the $'s...guess the don't like the old packaging ;-)

---

