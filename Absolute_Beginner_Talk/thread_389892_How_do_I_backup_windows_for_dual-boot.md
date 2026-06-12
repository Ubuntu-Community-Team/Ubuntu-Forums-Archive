---
title: "How do I backup windows for dual-boot?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by jdoben on 2007-03-21
Hello guys.  
How do I backup windows for dualboot?  I haven't found anything on or linked to this site about this.  I am wondering what software to use, preferably free.

Are there prefered methods for compatibility or ease?  As I understand it there is NTFS, FAT32, and Ext3.  NTFS is windows native and windows can read/write to all.  While Ubuntu 'reads' all three, it will currently only stabily write to Fat32 and its native Ext3.

Also,  I posted prior, asking for the links to the areas/sites to check for hardware compatibility.  I only got two responses both saying to just run the LiveCD.  This seems contrary to what seem to be long standing advices, maybe because prior linux distros didn't have this option.  Is this really a reliable way to go?
   I would really appreciate some additional guidance in what seem to be some of the more crucial elements involved with a smooth install.  

Thank you,
-JD
Dell Dimension L1000r
Motherboard x86 Dell CA810E
2 x 128MB SDRAM PCI33
Intel P3 996 MHz 
Mouse says intellimouse Explorer USB and PS/2 Compatible 
Additionally I have a wireless optical mouse and MS standard wireless key board(don't know if they work though)   
Don't know how find what drivers, etc

---

### Post by torgrot on 2007-03-21
If you only have one partition for windows, you can use the Backup tool in Windows.  You can only backup to a local location, i.e. an external hard drive not a network share.  If your NTFS partition is large the external drive will need to be formatted NTFS.  Fat32 has a file size limit of 4GB.  Make sure you create an Automatic System Recovery backup with the floppy to restore your settings and passwords.

LiveCD works reasonably well.  It allows you to boot into Ubuntu and try it out with out messing with your hard drives.

torgrot

---

### Post by profXavier on 2007-03-21
How much Harddrive space do you really have to work with, including any partitions you might have on those drives?

Thanks

---

### Post by overdrank on 2007-03-21
> **jdoben said:**
> Hello guys.  
How do I backup windows for dualboot?  I haven't found anything on or linked to this site about this.  I am wondering what software to use, preferably free.

Are there prefered methods for compatibility or ease?  As I understand it there is NTFS, FAT32, and Ext3.  NTFS is windows native and windows can read/write to all.  While Ubuntu 'reads' all three, it will currently only stabily write to Fat32 and its native Ext3.

Also,  I posted prior, asking for the links to the areas/sites to check for hardware compatibility.  I only got two responses both saying to just run the LiveCD.  This seems contrary to what seem to be long standing advices, maybe because prior linux distros didn't have this option.  Is this really a reliable way to go?
   I would really appreciate some additional guidance in what seem to be some of the more crucial elements involved with a smooth install.  

Thank you,
-JD
Dell Dimension L1000r
Motherboard x86 Dell CA810E
2 x 128MB SDRAM PCI33
Intel P3 996 MHz 
Mouse says intellimouse Explorer USB and PS/2 Compatible 
Additionally I have a wireless optical mouse and MS standard wireless key board(don't know if they work though)   
Don't know how find what drivers, etc

Hi I cannot speak on the free software for backup of windows but if you do a googgle search I am sure you will find something that will work for you. I would suggest just back up you documents and music, pics stuff that you want to have in the future. I have loaded ubuntu several times and had no problem. No on the compatibility of you hardware, the reason for running the live cd is that you will see if there are any problems between you system and the ubuntu. When you are running on  the live cd you dont not effect your current OS and  you can access the help files on ubuntu and find your hardware. Hope this helps. Good luck!

---

### Post by buuntuu! on 2007-03-21
welcome, 
backing up your fata from xp is quite easy, check out []("http://www.download.com/sort/3120-20_4-0-1-6.html?qt=backup&author=&titlename=&desc=&li=49&os=128&swlink=&gfiletype=") for various choices and recommendations.
window$ by default does neither read from nor write to ext3, but there are drivers that let it do so. [this one]("http://www.fs-driver.org/") works fine for me.
there is a good hardware compatibility guide [here]("http://doc.gwos.org/index.php/Main_Page")
and usually, if the live-cd works for you, installing will not be a problem (but if the live cd doesn't work it is not said that ubuntu can't be installed!) if you run into problems search the forums, it's unlikely that you are the first one to have them!
i would go for a lightweight-distro as you are a little low on ram, xubuntu should run fine on your box!
have fun

---

### Post by jdoben on 2007-03-21
Sorry I left some things out!
I have 74.5 GBHD  or so says MS 2k(5.00.2195 sp4).
I will check out that link but I feel better now  about using the CD.
Uubuntuu

---

### Post by jdoben on 2007-03-21
Sorry I'm have problems with my textbox every time I hover the mouse over it it shrinks.

Buuntuu do you think this back up will work for MS2k?
How do I know if I have fat32?  I thought I had NTFS, no clue though.  Auto Sys REcov where?  When you say floppy do mean I can use cd-rw's. I have nero will this work?  I think I have easyCD also.(My computer came second hand with alot of stuff on it)  Never used them though.

---

### Post by buuntuu! on 2007-03-21
i never had any problems with my backups on xp using simply safe, shouldn't be a problem with 2k either.
IF something fails and you need to recover your system, keep your Window$-cd ready
google for system recovery, you'll find howtos... don't ask me, i don't use window$ anymore ;)
read [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) for all the necessary info prior to installing. there is EVERYTHING you'll need to know about install, partitioning, filesystems...
using the live-cd is absolutely safe. you can even hit the install-icon and follow the install-steps nearly to the end before anything is really done to your hd, so do not fear.
just download the ubuntu-flavour of your choice, try it, read the link i posted and if you like what you see, welcome to the linux-world

---

