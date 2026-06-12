---
title: "Ubuntu dead"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Snoopy1966 on 2006-11-16
Hello,
OK here I am again with a problem similar to what I had before.  I have been trying to get wireless to work with the KDE desktop using the Linksys PCI G card. I changed my security settings of my router from my main computer.  Now when I try to boot into my desktop with Ubuntu it stops at Configuring network adapters.  I press Ctrl and C it starts to load stuff again and hangs at the same spot.  I got Ubuntu to load twice, but it says something about system died in start up.  I can not do anything at all now. I tried recovery mode, no luck there either.  I have three different kernels to choose from when I boot the systems.  Should I try one of those?  What can I do to repair Linux now.  What options do I have now?  I do not understand why I can not connect to a card that Linux sees and I can see the packages being sent and received in Networking tools.  
Any guidance would be greatly appreciated. :)

---

### Post by dillbertdabomb on 2006-11-16
is it at all posible to show the logs?  try to open them in liveCD
 
and how did you manage to kill ubuntu?

---

### Post by Snoopy1966 on 2006-11-16
Just boot the Live CD?  How do I get to my logs then once I get there?  I killed Ubuntu twice now by only changing something in my Wireless Network settings.  That is it, nothing else.  Quite frustrating.  

If I hook up my Ethernet cable to it will I get online?  I tried that already(not with Live CD) and it still would not load at the spot I mentioned.  

Could you tell me how I could use Live Cd to get the logs please.  I am pretty new and need as much help as I can get.  I got many things to work except this wireless ](*,) It is making me crazy :???: 

Thanks for the quick reply

---

### Post by mahy on 2006-11-16
Try editing /etc/network/interfaces (from a livecd, perhaps) and comment out everything regarding your wireless card. It should prevent the card from being configured at startup. Anyway, i find it hard to believe that some change in router settings bricked your computer. Look for other causes.

---

### Post by Snoopy1966 on 2006-11-16
> **mahy said:**
> Try editing /etc/network/interfaces (from a livecd, perhaps) and comment out everything regarding your wireless card. It should prevent the card from being configured at startup. Anyway, i find it hard to believe that some change in router settings bricked your computer. Look for other causes.

Run this from terminal then? /etc/network/interfaces
I will try Live CD now.  I have my 50 feet of Ethernet running through my apartment again.  I want to eliminate the cable.  It does not fly with my wife and 4 kids.  Even if I kept the cable how do you run it through an apartment without the managers getting upset that I ran it on the ceiling from the living room to the hall way.  Then I could at least nail it to the wall over the doorways. Not to mention how ugly that would be ;) 

I know I found a link somewhere about cards that will work with Dappper.  I have a Linksys WRT54G router and all I need is a PCI card that will work with it.  Can I use a different name like Belkin or something like that with the Linksys?  

OK here I go to Live CD.  Hopefully I can post from there and find out what I need to do to get to these logs.  

Really, I have a bricked cpu from network changes.  Two times it happened to me.  That is the only things I changed.

---

### Post by mahy on 2006-11-16
> **Snoopy1966 said:**
> Really, I have a bricked cpu from network changes.  Two times it happened to me. That is the only things I changed.

Bricked CPU?? I hope you mean bricked Ubuntu, coz i dunno how to fix CPUs. :mrgreen: Anyway, (sigh), you **can't** break down a computer changing something at your router. No you can't. Really. Can't. If you want some evidence, try reverting all the changes at your router and see if it helps cure the computer.

Anyway, if you wanna buy a new wifi card, there you go. I'd recommend something with PRISM or Atheros chipset.

---

### Post by Snoopy1966 on 2006-11-16
Ah yes Bricked Ubuntu not CPU
Anyway here I am in live CD now.  How can I access the logs?  I will try to change back my old settings in my router now too.  But I want to see these logs first and for you to see as well if there are indeed other problems.  Thanks :)

---

### Post by mahy on 2006-11-16
i know nothing about logs, that was the other guy's idea. I recommending editing your /etc/network/interfaces. Just make sure you edit the one on your hard drive, and not the one in the live filesystem. Look for /mnt/*something*/etc/network/interfaces

---

### Post by Snoopy1966 on 2006-11-16
> **mahy said:**
> i know nothing about logs, that was the other guy's idea. I recommending editing your /etc/network/interfaces. Just make sure you edit the one on your hard drive, and not the one in the live filesystem. Look for /mnt/*something*/etc/network/interfaces

Well I restored my router setting to exactly what they were before.  No dice there.  This is what the error was when it booted to Ubuntu:
The process for the system protocol died unexpectedly. 

I am using windows now to post this.  

How do I get to where you are talking about from Live CD to make sure I edit the log on the hard drive?

---

### Post by mahy on 2006-11-16
open the terminal

```
sudo cd /mnt/<something>

```
(replace 'something' with the name of your ubuntu partition).

```
sudo nano ./etc/network/interfaces
```
comment everything about your wireless network.

CAVEAT: this is not about logs.

---

### Post by Snoopy1966 on 2006-11-16
Hello
This does not work
sudo cd /mnt/dev/hda2
It says command not found

---

### Post by xpod on 2006-11-16
> I will try Live CD now. I have my 50 feet of Ethernet running through my apartment again. I want to eliminate the cable. It does not fly with my wife and 4 kids.

Hey i got a similar problem....
I got 100`s of feet of wire running all round the place here and my wife and five have just had to adjust....simple as that:mrgreen: 

They want computers with internets all over the place then thats just the way it has to be.......
Look on the bright side.......at least we aint got no wireless problems;)

---

### Post by That_Geek on 2006-11-16
if you want a new card, i would go with somethin from dlink, mine worked right from the start with no drivers or anything to install

---

### Post by Snoopy1966 on 2006-11-16
> **xpod said:**
> Hey i got a similar problem....
I got 100`s of feet of wire running all round the place here and my wife and five have just had to adjust....simple as that:mrgreen: 

They want computers with internets all over the place then thats just the way it has to be.......
Look on the bright side.......at least we aint got no wireless problems;)

How can I get me Ubuntu back though :(  I can not even use it now. 

>  if you want a new card, i would go with somethin from dlink 

The card will work with the Linksys router?

I need to fix my installation.  Can I install it again on the same partition?  I think it is trashed.

Anyone out there know how to fix my problem?
Thanks for the answers

---

### Post by Snoopy1966 on 2006-11-16
> **mahy said:**
> open the terminal

```
sudo cd /mnt/<something>

```
(replace 'something' with the name of your ubuntu partition).

```
sudo nano ./etc/network/interfaces
```
comment everything about your wireless network.

CAVEAT: this is not about logs.

These commands did not work from live CD.  Command not found.  Nano has no info at all.  Is my Ubuntu beyond repair?  
The process for the system protocol died unexpectedly
Can I fix this somehow?

---

### Post by Snoopy1966 on 2006-11-17
Anyone with some help to fix Ubuntu?  Is there a way to install it again in the same place?  Thank you.  What options do I have now?

---

### Post by Frak on 2006-11-17
> **mahy said:**
> Bricked CPU?? I hope you mean bricked Ubuntu, coz i dunno how to fix CPUs. :mrgreen: Anyway, (sigh), you **can't** break down a computer changing something at your router. No you can't. Really. Can't. If you want some evidence, try reverting all the changes at your router and see if it helps cure the computer.

Anyway, if you wanna buy a new wifi card, there you go. I'd recommend something with PRISM or Atheros chipset.
Believe it or not yes you can I've experienced it myself in fact I thank the people who told me how to fix it.
(Wireless using a desktop)

---

### Post by Snoopy1966 on 2006-11-17
OK Thanks How Do I fix it??? :confused: 
I have been searching and I really do not find any clear answers to my problem.  I need some guidance, I am to much a newbie to know what is going on yet.  Is there a fix it guide somewhere?

---

### Post by bonjun on 2006-11-17
> [QUOTE]Code:
sudo cd /mnt/<something>

sudo nano ./etc/network/interfaces  <--- check this please

comment everything about your wireless network.[/QUOTE]

because it is entirely different from this one:
> sudo nano /etc/network/interface

or is it /<ubuntu_on_harddisk>/etc/network/interface
that is if you are running LiveCD and comment out everything about your wireless card/network

---

### Post by Jussi Kukkonen on 2006-11-17
> **Snoopy1966 said:**
> These commands did not work from live CD.  Command not found.  Nano has no info at all.  Is my Ubuntu beyond repair?  
The process for the system protocol died unexpectedly
Can I fix this somehow?
Snoopy, take it easy: Do things slowly, think about the error messages you get (maybe you can figure out what they mean), and most importantly: *copy-paste everything from the terminal when you have problems.* In this case copy the command prompts, the commands you used and the exact outputs you got and paste them here. People may be able to help, but only if you give them the information they need.

---

### Post by Snoopy1966 on 2006-11-17
> **bonjun said:**
> because it is entirely different from this one:


or is it /<ubuntu_on_harddisk>/etc/network/interface
that is if you are running LiveCD and comment out everything about your wireless card/network

The only way I can get into Ubunto is Live CD right now.  When I try to load it without it I get the error
The process for the system protocol died unexpectedly

How do I do this?
<ubuntu_on_harddisk>/etc/network/interfacewould it be like this?
ubuntu/dev/hda2/etc/network/interface
If I do that Command not found is the result

sudo nano ./etc/network/interfaces <--- check this please
No information shows up at all

> People may be able to help, but only if you give them the information they need.
I wish I could find this info.  I am using Live CD to try to repair this mess I made.

OK I got this to work

```
 sudo fdisk /dev/hda

The number of cylinders for this disk is set to 9726.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```

Then I did this

```
Command (m for help): v
1934 unallocated sectors

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```

OK I did this and I believe this is my Ubuntu partion from looking at Disks

```
ubuntu@ubuntu:~$  sudo fdisk /dev/hda2
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 28862.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): l

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot
 1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT
1c  Hidden W95 FAT3 75  PC/IX

```

Do I use w now to write and start over now from this point?

---

### Post by Snoopy1966 on 2006-11-17
Is there any suggestions for me to try?  I have no clue in what to do at this point.

---

### Post by Snoopy1966 on 2006-11-17
OK I think I am going to get a wi fi card with prism or Atheros chip.  Do a full install of Kubuntu, or maybe Debian.  I have the Kubuntu CD , Ubuntu CD, and the Debian minimum CD to start installation.  
Which is better.  Kubuntu, Ubuntu or Debian?  Ubuntu is based on Debian correct?

---

