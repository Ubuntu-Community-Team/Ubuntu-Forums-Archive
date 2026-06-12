---
title: "Help uninstalling Ubuntu on Mac OS X"
date: 2010-01-24
forum: Apple Hardware Users
---

### Post by TehLove on 2010-01-24
I need to uninstall Ubuntu on my Mac which is running OS X Version 10.6.2

I installed it via a live disk and boot camp(I made a partition for Windows and used that). The faster I can get help, the better. I want to install Windows 7 via boot camp and I am not able to. 

Thanks all! ~TehLove

PS: Feel free to add me on MSN or E-mail me at [email]TehLove@rsbot.org[/email]


[COLOR="Red"]**UPDATE**[/COLOR]


This is my rEFit report.

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    420253423  Mac OS X HFS+
 3      423772200    423774153  EFI System (FAT)

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    488397167  ee  EFI Protective

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 423772200:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type EFI System (FAT)


[B][COLOR="Blue"]At this point, I just want all the extra partitions except for my Mac HD(of course)
[/COLOR][/B]

---

### Post by linuxopjemac on 2010-01-24
Cannot you delete the partition from within the liveCD (gparted) and format it Fat32...I don't know how bootcamp works, but it might then see a partition which is ready for Windows

---

### Post by TehLove on 2010-01-24
I will try that in a moment. Boot Camp is a utility by Apple that just handily partitions the disk for you. After that, you're on your own LOL.

And what do you mean by "gparted"? I have the liveCD that I am going to put in(after I finish burning this ISO on to a CD) ready.

---

### Post by TehLove on 2010-01-24
I tried using my Ubuntu disk to see if there was a uninstall option and there isn't. I also tried putting in my Mac OS X Installation CD and that wouldn't let me install on my hard disk.

Please, someone tell me if there is a way to just totally rid my system of Ubuntu. Thanks

---

### Post by ibuclaw on 2010-01-24
Why people expect there to be an uninstall feature frankly startles me even to this day.
You can still boot into OSX, right? If not, you can open a terminal via the OSX installation CD.

Restore the bootloader - [http://www.insanelymac.com/forum/index.php?showtopic=57650&st=0&p=412541&#entry412541](http://www.insanelymac.com/forum/index.php?showtopic=57650&st=0&p=412541&#entry412541)

Then just delete the partition...

---

### Post by TehLove on 2010-01-24
Maybe I understood you wrong or maybe you understood me wrong. I can easily get into both Mac OS X and Ubuntu, it's just the fact that I don't want Ubuntu anymore and Boot Camp won't let me make more partitions.

How do I delete the partition Ubuntu is on and put all the memory it contains back into my main OS X one?

---

### Post by woodmaster on 2010-01-24
> **tinivole said:**
> boot into OSX
 
Restore the bootloader - [http://www.insanelymac.com/forum/index.php?showtopic=57650&st=0&p=412541&#entry412541](http://www.insanelymac.com/forum/index.php?showtopic=57650&st=0&p=412541&#entry412541)
 

 
Then, boot off Ubuntu Live CD(Not the Ubuntu install on your Box.)  Use Gparted(a partitioning program under System tab) to delete your Ubuntu partition.  Reformat it as Fat32 filetype.  Install Windoze...if you must.

---

### Post by TehLove on 2010-01-24
Before reading what you said, I went into Disk Utility and I totally wiped the disks. Now my only option when I boot is Mac. How do I merge the now blank partitions with my original Macintosh part? Here is a pic. 

[IMG]http://i991.photobucket.com/albums/af40/xaviera0929/screen-capture-14.png[/IMG]

Here is a picture of my Boot Camp.

[IMG]http://i991.photobucket.com/albums/af40/xaviera0929/screen-capture-1-5.png[/IMG]

---

### Post by woodmaster on 2010-01-24
U can still boot off the live CD.  The power of gparted will let you merge/format/delete... all that you need to do with partitions.

---

### Post by jbiggs12 on 2010-01-24
Boot off of your livecd, go into gparted, delete your ubuntu partitions (if you want to back your ubuntu up, then back it up before this step) and then create a FAT32 partition with the remaining space... that should do the trick.

---

### Post by TehLove on 2010-01-24
When I get home I will try with the liveCD. I'll tell ya if it works. Is there any way to do it within OS X? It'd be easier. Because right now I just have two random partitions. One has ~40gb and the other has ~1gb. Is there any way to just merge them with my Mac part(Within OS X of course).

---

### Post by woodmaster on 2010-01-24
IDK ne thing bout Mac.  It's easy to merge them with gparted.

---

### Post by TehLove on 2010-01-24
What is "gparted"?

I'm going to Google it but it would be nice if someone could post a simple explanation.

---

### Post by adam814 on 2010-01-25
GParted is an open-source application for dealing with partitions/filesystems.  You access it in the LiveCD under System > Administration > GParted (I believe I've also seen it as Partition Editor there).

Unfortunately it won't let you merge those two partitions back into your other Mac partition because it can't "grow" hfs+ partitions.  It can create, shrink, copy, move, or check them, but it can't expand an existing one to fill available space.  You could use GParted to remove them or merge them into a single NTFS partition ready to install Windows into.

I don't have a Mac so I'm not sure what capabilities it has to do what you need (Windows XP will not without commercial software, Vista and 7 can on their own).

---

### Post by TehLove on 2010-01-25
Thanks for trying!

---

### Post by SparkyRacer on 2010-01-26
For what it's worth, I was having a similar problem where I just wanted to get rid of an extra partition left over from installing another OS under BootCamp.  When I tried to use the BootCamp Utility to remove it I'd get the same error.  It turns out that BootCamp Utility won't touch a partition if it doesn't know what it is so I just used Disk Utility to format that partition as FAT32 , restarted BootCamp Utility and suddenly all was right with the world.

---

