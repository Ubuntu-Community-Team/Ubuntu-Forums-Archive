---
title: "installed ubuntu, windows gone"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by viky on 2008-01-18
PLease could any one tell me is ther any way to recover windows partition. I installes ubuntu, while i said use all space. Please someone help me to get all my valuable windows files from ubuntu. Please some0one help me.

---

### Post by CCNA_student on 2008-01-18
So when you were installing Ubuntu you gave the Ubuntu partition all of your hard drive? If this is what you did, your data may be lost. I know that there are ways to get lost data, but I do not know what they are. All I can suggest if you did this is to look around the forums or call a computer repair shop.

---

### Post by eolson on 2008-01-18
Did you use the default option on the install disk or did you scroll down and take one of the later options?

---

### Post by JimRaynor on 2008-01-18
wow im glad i checked the forums, was about to install my 7.1 cd for a dual boot system, under step 4of7 "Prepare disk space" it gives 3 options

Guided - use entire disk
      SCSI sda 30gb etc...
Guided - use the largest continuous free space
Manual

Sounds like I would be in the same boat if i selected the first option... so which do i choose? The second one? Or do I need to create a partition in windows before itll show up in this list. Thanks for any help

---

### Post by thelatinist on 2008-01-18
> **viky said:**
> PLease could any one tell me is ther any way to recover windows partition. I installes ubuntu, while i said use all space. Please someone help me to get all my valuable windows files from ubuntu. Please some0one help me.

If you told it to use the entire disk, then there is no way to recover your Windows files.  I am sorry.

---

### Post by JimRaynor on 2008-01-18
Step nine of the quickguide sticky... :(

---

### Post by CCNA_student on 2008-01-18
Do you know how big the free space is? If it is at least 4GB you could install on that. The manual partitioning might be better for you. I posted Instructions for my Linux User's Group at [http://wheatlandlinux.wordpress.com/instructions-and-how-tos/]("http://wheatlandlinux.wordpress.com/instructions-and-how-tos/")
Good luck.

     Sin Cere,

     CCNA

---

### Post by CCNA_student on 2008-01-18
> **thelatinist said:**
> If you told it to use the entire disk, then there is no way to recover your Windows files.  I am sorry.

Not quite true. There are tools that can recover files, but you will have to go to a computer repair shop and pay some money. One day in my Cisco class a man who worked at a computer repair shop managed to get data of a bad hard disk. It took him about 15 hours to do so.

---

### Post by Espreon on 2008-01-18
Oi, your data is likely to be gone forever. I hope you did not lose any important things like work related stuff or treasured memories. Always BACKUP!

---

### Post by eolson on 2008-01-18
usb sticks are inexpensive easy to use and hold a lot of data.  It's a bit late,  but for future reference.

---

### Post by christopher.newell on 2008-01-18
The option you chose could mean all the difference, but I suspect your best bet is to find an undelete tool and be prepared for lots of lost data.  If you allowed Ubuntu to reformat, then there's a slim chance that the information is still there, but without a File Allocation Table, your computer can't find it.  That's where the undelete comes in.  If the Ubuntu install wrote over the spaces where your data was, then to my knowledge, it's gone.
In reply to thelatinist, I consider myself very knowledgeable about Windows (I thought I was good with computers in general until I installed Ubuntu!), so I took a risk and chose the manual option.  I think I made the best choice.  There is some help along the way, so I'd recommend that option.  If something doesn't seem right, don't proceed.  I almost allowed my windows installation to be wiped as well.
I know this is a case of too-little-too-late, but I've been running a dual-drive system for years.  Windows went on one drive, and all my documents, favourites, media files, etc went on another.  That way when I reinstalled Windows, I only had to back up my Outlook data.  I learned the hard way--by losing everything, then doing it again a year later!

---

### Post by thelatinist on 2008-01-18
> **CCNA_student said:**
> Not quite true. There are tools that can recover files, but you will have to go to a computer repair shop and pay some money. One day in my Cisco class a man who worked at a computer repair shop managed to get data of a bad hard disk. It took him about 15 hours to do so.

This is true, it may be possible to retrieve data, but do do so is very time consuming and prohibitively expensive.  Unless the OP is very wealthy or his data very valuable, it is for all intents and purposes gone.

---

### Post by JimRaynor on 2008-01-18
i do not mean to hijack your thread viky

> **CCNA_student said:**
> Do you know how big the free space is? If it is at least 4GB you could install on that. The manual partitioning might be better for you. I posted Instructions for my Linux User's Group at [http://wheatlandlinux.wordpress.com/instructions-and-how-tos/]("http://wheatlandlinux.wordpress.com/instructions-and-how-tos/")
Good luck.

     Sin Cere,

     CCNA


when i openthe partition editor when booting from the live cd, i see this

/dev/sda1   fat16    47.03MiB  7.40 MiB-Used     39.64Mib-unused
/dev/sda2   ntfs      24.23GiB   12.88Gib-Used    11.35Gib-unused  boot
/dev/sda3   fat32    3.66GiB    3.33Gib-Used   343Mib-unused
unallocated        7.84Mib

i cant make heads or tales of whats currently being used by xp :confused:.  I suppose all of it, ill check out your guide

---

### Post by louieb on 2008-01-18
Two things to try:
[TestDisk and PhotoRec]("http://www.cgsecurity.org/wiki/TestDisk")
[SystemRescueCd]("http://www.sysresccd.org/Main_Page")
I been lucky and haven't had to use them.  But there are post on this forum  saying that testdisk and  photorec have recovered data for them after reformating a drive.  The system rescue CD contains testdisk.

---

### Post by iansane on 2008-01-18
> **CCNA_student said:**
> Not quite true. There are tools that can recover files, but you will have to go to a computer repair shop and pay some money. One day in my Cisco class a man who worked at a computer repair shop managed to get data of a bad hard disk. It took him about 15 hours to do so.

data can be retrieved off of a bad hard drive but I think it is a different situation when another os actually formats and writes over it. I think the only way possible would cost hundreds if not thousands of dollars and the average computer repair person wouldn't have the knowlege or software and equipment to do it.

I learned the hard way too. Make sure you know your drives and partitions like the back of your hand before you start and back up back up back up. I could be wrong and I hope I am. Sorry you lost your data

---

### Post by CCNA_student on 2008-01-18
> **JimRaynor said:**
> i do not mean to hijack your thread viky




when i openthe partition editor when booting from the live cd, i see this

/dev/sda1   fat16    47.03MiB  7.40 MiB-Used     39.64Mib-unused
/dev/sda2   ntfs      24.23GiB   12.88Gib-Used    11.35Gib-unused  boot
/dev/sda3   fat32    3.66GiB    3.33Gib-Used   343Mib-unused
unallocated        7.84Mib

i cant make heads or tales of whats currently being used by xp :confused:.  I suppose all of it, ill check out your guide

Windows XP is on the NTFS partition. The FAT32 partition must be a recovery partition. And I have no idea as to why an FAT16 partition would be on a computer made in the last ten years. If you have the recovery discs that came with your system you can delete the FAT32 3.66GB partition and shrink the NTFS partition by a few GB If you want Ubuntu. Select the manual option and follow the instructions I gave you in that link to my Linux blog. And make sure you back up all important data. Things usually do not go wrong, but they still can. I hope this answered your question.

     Sin Cere,

     CCNA

---

### Post by iansane on 2008-01-18
> **JimRaynor said:**
> i do not mean to hijack your thread viky




when i openthe partition editor when booting from the live cd, i see this

/dev/sda1   fat16    47.03MiB  7.40 MiB-Used     39.64Mib-unused
/dev/sda2   ntfs      24.23GiB   12.88Gib-Used    11.35Gib-unused  boot
/dev/sda3   fat32    3.66GiB    3.33Gib-Used   343Mib-unused
unallocated        7.84Mib

i cant make heads or tales of whats currently being used by xp :confused:.  I suppose all of it, ill check out your guide

you should be able to boot into windows and go to "my computer" check the size and file system type of the drives there. If I had to guess I would say the ntfs one is the one with xp but it could be one of the FAT partitions. That list just means that on drive sda you have 3 partitions and 7.84 Mb of unallocated (unpartitioned space) Actually, now that I look again, the fat32 is not big enough for XP's recomended size and the fat16 definately isn't so it would have to be the ntfs (sda2) you just need to see if you installed any programs to the other partition instead of the default root windows root (same drive as windows) otherwise they are probably just storage space or recovery files in the fat16 partition.

---

### Post by Methuselah on 2008-01-18
I think the installation is a little misleading because 'guided' installation doesn't actually guide you it  just uses the whole disk. I remember selecting guided and seeing something afterwards that suggested the installation was going to use the whole disk and so I backed out of it and created the partitions myself.

---

### Post by louieb on 2008-01-18
> **JimRaynor said:**
> ...
/dev/sda1   fat16    47.03MiB  7.40 MiB-Used     39.64Mib-unused
/dev/sda2   ntfs      24.23GiB   12.88Gib-Used    11.35Gib-unused  boot
/dev/sda3   fat32    3.66GiB    3.33Gib-Used   343Mib-unused
unallocated        7.84Mib
i cant make heads or tales of whats currently being used by xp ...

Hello Jim
sda1 and sda3 are probably recovery and  backup partitions these are commonly used by some computer makers such as Dell, IBM .... sda2 is your XP install.     

Your situation is quite a bit different from viky's.  Your better off starting your own thread. Be sure to include you computer make, model, amount of memory. Your kind of tight on disk space  and your going to need two more partitions for Linux. That space has to be taken from somewhere.

---

### Post by Beowulf15 on 2008-01-18
> **christopher.newell said:**
> The option you chose could mean all the difference, but I suspect your best bet is to find an undelete tool and be prepared for lots of lost data.  If you allowed Ubuntu to reformat, then there's a slim chance that the information is still there, but without a File Allocation Table, your computer can't find it.  That's where the undelete comes in.  If the Ubuntu install wrote over the spaces where your data was, then to my knowledge, it's gone.
In reply to thelatinist, I consider myself very knowledgeable about Windows (I thought I was good with computers in general until I installed Ubuntu!), so I took a risk and chose the manual option.  I think I made the best choice.  There is some help along the way, so I'd recommend that option.  If something doesn't seem right, don't proceed.  I almost allowed my windows installation to be wiped as well.
I know this is a case of too-little-too-late, but I've been running a dual-drive system for years.  Windows went on one drive, and all my documents, favourites, media files, etc went on another.  That way when I reinstalled Windows, I only had to back up my Outlook data.  I learned the hard way--by losing everything, then doing it again a year later!

You're spot on in terms of the using tools to try and grab it.  As long as no new data has been written over most of the drive, you'll most likely be able to salvage some of your data.  Just try not to panic and delete anything else.

---

### Post by Sinkingships7 on 2008-01-18
there is a way to get your files back. maybe not all, or maybe not any. when ubuntu installs, it doesn't format the hard drive. the more data you allow to be written to your hard drive, the higher your chances are of losing your data, for it will be over written. there are complicated ways to retrieve "lost data" if the drive hasn't been formatted. if you hook your drive up as a slave on another computer, and assuming your data hasn't been overwritten, you may be able to recover some things. i know that isn't a very promising answer and is full of "maybe's/if's/possibly", but it's the best chance you have. if you don't know much about what i'm talking about, you should get your computer to someone who does, and try not to mess with it as much as you can.

---

