---
title: "Very Odd Installation Problem"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by zoob on 2005-09-17
Hi,

I am new to Linux and wonder if someone can point me in the right direction to trouble shoot my problem.

System

Intel D845BG motherboard
Intel 2.5GHz Processor
512MB RAM
Maxtor 6Y080L0 - 
Partitioned and formatted NTFS. Windows XP Pro SP2
C: = System D: = Data jumpered as Master

Maxtor 6Y080L0 - ubuntu Linux with grub
jumpered as Slave

Lite-On JMS XJ-166S DVD-ROM drive
jumpered as Master

Lite-On DVDRW SOHW-1633S DVD-RW
jumpered as Slave

PCI USB 2.0 Card
IEE1394 FireWire Card
Hauppage WinTV Card
SB Live! Value Edition
External SimpleTech 160GB USB HDD
Apple Ipod 15GB
HP 990c Printer
HP 3400c Scanner
Motorola USB Cell phone cradle

This setup was working flawlessly under Hoary & Breezy dual booting with grub.  It was acting in Windows like the first Maxtor drive was heading south so I replaced it with a Seagate ST380011A HDD.  I also replaced the DVD-ROM as it was not occasionally not reporting itself in BIOS or Windows XP.  I ghosted the data from the Maxtor to the Seagate knowing I would have to reinstall ubuntu to fix the grub.

I installed Breezy and all went well until shut down when Breezy scrolled text after the shutdown command.  Then on reboot it would hang at Creating hotswap.  If I let it go 5 minutes it text scrolled again.  I installed and reinstalled at least 4 times.

I grabbed my Hoary CD.  Installed okay it hung at a different spot on installation.  Finally installed it but it blows up in the very same now too.  I think the text that I can see is saying something about clearing interrupts.  Every time I installed I repartitioned, formatted and reinstalled grub.

Windows works better than it has in a long time but I miss my ubuntu.  I was just starting to get familiar with Linux as ubuntu was the most friendliest version I have ever run.  Does anyone have an idea of where I should start short of wiping out my XP drive which I need so dearly?  Any suggestions would be helpful.  Thanks.

zoob

 ](*,)

---

