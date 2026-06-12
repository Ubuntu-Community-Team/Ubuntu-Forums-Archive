---
title: "OMG I'm in trouble!!!!"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by skiwithpete on 2007-08-25
I downloaded Ubuntu, and decided to use partition magic (in XP) to change the partition.  Part way through it failed, and now can't boot and just keeps going to BSOD and rebooting.  

The only thing that works is the LIVECD of Ubuntu I'm using now.

I can't mount the drive.


In details it says: 

 
Mount: wrong fs type, bad option, bad superblock on /dev/sda1  missing codepage or other error  In some cases info is found in syslog - try dmesg | tail or so.

I have no idea how to use Linux!!!  I'm lucky I got firefox to work.

Please help.  I can't lose all the stuff on C:  PLEASE.

P

---

### Post by HotShotDJ on 2007-08-25
Hmmm... so the polite but firm warning that partition magic gives you regarding backing up your important data before messing with partitions went ignored?  I cannot promise you that the following will save your data -- but it may be your best option: [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  I used it to recover data from a repartitioned and reformatted hard drive after learning MY lesson about redundant backups the hard way.  WARNING:  It is NOT the easiest program in the world to use.  READ THE MANUALS AND UNDERSTAND THE INSTRUCTIONS FIRST!!!   But it is by far the most powerful recoveyr tool.

You'll need to download a LiveCD of [RIP Linux]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip") (or any distro that includes TestDisk on the live cd -- ubuntu does NOT have this tool), burn it and boot to it in order to use TestDisk.

---

### Post by oilchangeguy on 2007-08-25
also try to boot the computer into safe mode. press f8 repeatedly as soon as the computer starts, select the option for safe mode, nothing else. if you can get into windows (use the admin id at the sign-on screen) back up all of your data. then try to do a system restore. other wise you may be sol.

---

### Post by EvKat on 2007-08-25
Hmhm, I tried dual booting Ubuntu with XP once, I´ve been down that familiar horrifying road, except for the fact that I trashed my MFT from partitioning incorrectly.

As aforementioned, try booting into safe mode to see if you can backup data that is still recoverable and go from there; usually, if you still can´t get in regardless, you could siphon data from the HD if it´s used as an external. What type is it? RAID? SCSI?

Did you set your BIOS to be configured for a dual boot environment?
Did you create the necessary amounts of partitions (for swap space, etc) and allocate enough space to them?

---

### Post by HermanAB on 2007-08-25
Try to boot a Live CD such as Knoppix and try to copy your Windows data to a stack of CDs/DVDs.

Knoppix is also a Debian distribution like Ubuntu, but its ability to figure out weird hardware is better.  Knoppix is primarily designed as a test and repair CD, so all the tools you can imagine are on there.  No Geek should be without a Knoppix CD in his tool box.

Hope that helps!

Herman

---

### Post by Majorix on 2007-08-25
> **HermanAB said:**
> Try to boot a Live CD such as Knoppix and try to copy your Windows data to a stack of CDs/DVDs.

Knoppix is also a Debian distribution like Ubuntu, but its ability to figure out weird hardware is better.  Knoppix is primarily designed as a test and repair CD, so all the tools you can imagine are on there.  No Geek should be without a Knoppix CD in his tool box.

Hope that helps!

Herman

You can't burn CDs with Knoppix CD in. But you could try to do move stuff to an external HDD.

---

### Post by ddrichardson on 2007-08-25
Before you go any further, image the disk. If you tinker and make things worse you are definately scuppered. Try [System Rescue CD]("http://www.sysresccd.org/Main_Page")

Once you've done this you need to determine what needs to be rescued - I'm assuming you're concentrating on your Documents.

There are lots of good tools for recovery out there - but most will not be able to restore the filename correctly, so you may find you need to spend time working out whats what.

---

### Post by HotShotDJ on 2007-08-25
> **ddrichardson said:**
> Before you go any further, image the disk. If you tinker and make things worse you are definately scuppered.This is probably the best comment in this thread.  Whichever course you decide to try, you run the risk of further damaging your files.  [PartImage]("http://www.partimage.org/Main_Page") is the utility you will use on SystemRescueCD (I believe it is also included with RIP Linux -- in fact, TestDisk might be on SystemRescueCD, so either one will do).  In anycase, I am in full agreement with ddrichardson -- do not begin ANY of the above procedures without creating an image of your drive or you may find yourself making the situation worse than it already is.

---

### Post by the_darkside_986 on 2007-08-25
Never use Partition Magic. The one that is freely downloadable is flawed and will wreck your whole disk setup. 

The ONLY safe way to resize a Windows drive in my experience is the openSUSE Linux installer. But you should always defrag the Windows drive a few times and backup data before attempting it.

GParted liveCD is very good too but I don't know if I even trust it to safely repartition the drive.

---

### Post by asmoore82 on 2007-08-25
> **the_darkside_986 said:**
> GParted liveCD is very good too but I don't know if I even trust it to safely** repartition the drive**.

I think you meant to say "resize NTFS" there or everyone who isn't using *x.xx* version of OpenSuSE is screwed! :lol:

anyways, i've said it before and i'll say it again ... 

IMHO, all non-*NIX partitioning software is crap. ESPECIALLY *magic.

---

### Post by steve.horsley on 2007-08-25
> **ddrichardson said:**
> Before you go any further, image the disk. If you tinker and make things worse you are definately scuppered. Try [System Rescue CD]("http://www.sysresccd.org/Main_Page")


I'll second this. If your data is that important, it's worth buying an external hard disk bigger than your internal one to save the image to.

---

### Post by rrcn on 2007-08-25
**There is a better way**, you can use windows to fix your problem.  You will need to use someone else's computer for this set-up and to burn your iso file, but you will be able to retrieve all of your data, maybe even fix your XP installation.  Go to [http://www.ubcd4win.com/](http://www.ubcd4win.com/), and read carefully.  While the process may look a little involved its only a matter of following the instructions.  Really no need for me to go into any more detail, feel free to email me if I can help further, I keep an XP computer for the purpose of updating UBD4W, to repair folks pcs.

---

### Post by skiwithpete on 2007-08-25
In linux, still with ubuntu.

I can't mount the disk, so I don't know how I would take an image of it.

I have a hard drive that is large enough it could take it, but I still don't get a how I would see the data/image - let alone get the ExternalHD to work in Ubuntu.

Thanks for your help, if it changes things, I was partitioning the end of the drive, not the start of it, so there shouldn't be much data that far out on the disk.

Cheers,

P

---

### Post by HotShotDJ on 2007-08-26
> **skiwithpete said:**
> I can't mount the disk, so I don't know how I would take an image of it.

That is perfectly all right.  You don't want to use any of the Linux tools mentioned on a mounted partition anyway.  PartImage will make an image of your unmounted disk.

---

### Post by southernman on 2007-08-26
+1 SystemRescue CD

It has another nifty tool on it called "Testdisk" which will not only analysis your hard drives, but if it finds hidden or previously deleted partitions, it will allow you to copy the files from those partition(s).

I spent around 2 days playing with that program running test on some bad drives I had... managed to copy off some 18GB worth of previously lost files.

+1 Partimage

Another great tool to have and use.

Good Luck... I hope you get your files back.

---

### Post by steve.horsley on 2007-08-26
To take an image of the disk using a Linux live CD, use the command **dd** - short for Disk Dump I think. 
Assuming your troublesome disk is /dev/hda, and your external disk is mounted as /media/USBDISK, use ihis command:
**dd if=/dev/hda of=/media/USBDISK/hda.img**
if is InputFile, and you specify the whole hard disk
of is the output file, and we write to a standard file on the external drive. This images your entire drive, partition table and all. 

Now you can mess with the hard drive using any tools you want without fear of permamntly making things worse. You can restore the image to the hard disk with the command:
**dd if=/media/USBDISK/hda.img of=/dev/hda**
You need to have root priviledge to use dd this way, so if you're using teh Ubuntu live CD, use the command 
**sudo -i **
to raise your priviledge first.

There are rescue CDs around that cah recover from a corrupt partition table by looking at the disk contents and working out from the disk contents where the partitions were. I can't remember the name though. It may well be the SystemRescue CD others are recommending.

---

### Post by skiwithpete on 2007-08-27
Ok, Am still in Ubuntu 7.04 LiveCD.  I want to back up the HDD before I try anything.

First, I can't get the USB drive to mount.  I plugged it in, but nothing has happened.  I don't know how to make it visible.

Secondly, I can anticipate a problem with the dev/hda path suggested to back up the drive.  Because when I click on the drive it says dev/hda not recognized.  Also when I browse to File System / dev/ in Ubuntu, there is no hda folder.

Please, I need step by step help on this, I have no idea how to use Ubuntu.

P

---

### Post by vincentvee on 2007-08-27
yeah most win based partitioning software is crap....i wonder if this guy can install buntu from the live disc, resizing the win partition, then copy all his files over to his shiny new ext3 partition, then when he has everything he needs, he can reformat ntfs??
think i went through a similar thing when i dual booted XP ubuntu 5.10
long time ago, but i'm sure thats what i did in the end

V
:confused:
> **asmoore82 said:**
> I think you meant to say "resize NTFS" there or everyone who isn't using *x.xx* version of OpenSuSE is screwed! :lol:

anyways, i've said it before and i'll say it again ... 

IMHO, all non-*NIX partitioning software is crap. ESPECIALLY *magic.

---

### Post by skiwithpete on 2007-08-27
Vincentvee,

Its like no one understands that I can't see the drives!

Even when I plug in the USB.  I see nothing.  

I don't know how to see onto my NTFS partition, because it can't mount it.  I keep saying the same things.

I can't see dev/hda1 or dev/hda How the hell am I meant to get the data off it, let alone onto my USB drive that I can't see!!!

P

---

### Post by ddrichardson on 2007-08-27
We do understand - but you aren't providing any helpful information. When in the live cd what is the output of ```
sudo fdisk -l
```?

---

### Post by skiwithpete on 2007-08-27
Here is the output.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13900   105083968+   7  HPFS/NTFS
/dev/sda2           13901       20673    51203880    f  W95 Ext'd (LBA)
/dev/sda5           13901       20673    51203848+   7  HPFS/NTFS


The USB drive is not plugged in.

Before I started mucking with it, I had a c drive of 100gigs and partioned X drive of 50gigs.  I tried to resize the C drive to accomodate linux.

P

---

### Post by steve.horsley on 2007-08-27
This is looking good. Your drive is /dev/sda (not hda). But it's there and we can see the partitions. /dev/sda1 is an NTFS partition, 105GB. This will be C:. /dev/sda2 is an "extended" partition, which acts as a container for logical partitions, its size is 51GB, roughly. It contains one logical partition, /dev/sda5, which is a 51GB NTFS partition and will be the next partitions Windows sees - probably D:.

So we confirm that your hard drive is there. You can try and mount it and look at the contents if you like. (I assume you're using the Ubuntu live CD) Open a terminal (Programs->Accessories->Terminal) and do the following:
First, you must gain the required priviledges:
**sudo -i**
This changes your promts from a $ to a #, showing you have full admin rights.
Next, make a folder for the disk contents to appear in:
[B]mkdir /media/C
mkdir /media/D
[/B]
Now try and mount the partitions
[B]mount /dev/sda1 /media/C
mount /dev/sda5 /media/D[/B]
If all goes well, you should have a couple of icons C and D on your desktop, and you can double-click them and see files inside. This will demonstate that your data is there and could be recovered.

The next problem is what to copy the contents to. You say you have an external drive but you can't see it. I assume it's formatted NTFS, but let's see. Try plugging the USB drive in again, wait a few seconds, and then try the command 
**sudo fdisk -l **
again. See if we get another drive listed this time. It may show up as /dev/sdb for instance. If it does, you should be able to mount it the same way as you did the hard drives above. The trouble is that Ubunto cannot normally write to NTFS partitions (writing to FAT is not a problem, but MS won't release the details of NTFS so it has to be reverse engineered, and writing to it is only recently developed). You will need to install the ntfs-3g drivers to gain write access to NTFS. I've not done this myself, so hopefully someone else can fill in some instructions there. If you had a FAT external disk, it would probably appear on the desktop as soon as you plugged it in.

Try this out and let us know how you get on.

---

### Post by skiwithpete on 2007-08-27
This is what happens:

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir /media/C
root@ubuntu:~# mount /dev/sda1 /media/C
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Also, I've plugged in the USB HDD, but there is no change to anything.  It still reads:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13900   105083968+   7  HPFS/NTFS
/dev/sda2           13901       20673    51203880    f  W95 Ext'd (LBA)
/dev/sda5           13901       20673    51203848+   7  HPFS/NTFS

Am 100% positive that the USB drive is FAT btw.

Let me know what next.

P

---

### Post by skiwithpete on 2007-08-27
Got the USB to mount.  All of a sudden it just appeared on the desktop.  So I tried a tip to create an image BUT IT DIDN"T WORK.  Look below

root@ubuntu:~#  sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13900   105083968+   7  HPFS/NTFS
/dev/sda2           13901       20673    51203880    f  W95 Ext'd (LBA)
/dev/sda5           13901       20673    51203848+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

root@ubuntu:~# dd if=/dev/sda1 of=/dev/sdb1/sda1.img
dd: opening `/dev/sdb1/sda1.img': Not a directory

So I looked, and the USB drive is also /media/Toshi250/ so I tried this:

root@ubuntu:~# dd if=/dev/sda1 of=/media/Toshi250/sda1.img
dd: opening `/media/Toshi250/sda1.img': Read-only file system
root@ubuntu:~# 


What have I done wrong?  I feel I'm really close to backing this up, and once I've done it, i'll boot SystemRescueCD and use testdisk to try to recover some data.

---

### Post by steve.horsley on 2007-08-27
Firstly, you seem to be trying to image /dev/sda1 which is the windows partition only. If you have the space, it may be better to image /dev/sda which is the entire drive. 

Secondly, the output file should be sent to the mounted drive (/media/blah) not the raw device /dev/sdb. Your second try was right.

Thirdly, you are getting told it's a read-only system because Ubuntu cannot write NTFS by default (otherwise you would have succeeded in taking an image). You need to install the ntfs-3g drivers before you can write to NTFS partitions. See this tutorial (I haven't tried it myself, but it looks good)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

P.S. Don't consider changing your external drive to FAT to write the image to because FAT can't hold files larger than 4G, I think.

---

### Post by Marat Galiev on 2007-08-27
NTFS write support disabled in Ubuntu by default.
You must go to packages.ubuntu.com
and find packages,named ntfs-3g,ntfs-3g-config.
After install,you can mount you partitions with GUI tool.
or mount you partitions like this:
```

/dev/sda1    /mnt/winxp    ntfs-3g    uid=1002,gid=100,umask=0022    0 0
/dev/sda5    /mnt/winxp    ntfs-3g    uid=1002,gid=100,umask=0022    0 0

```

---

### Post by skiwithpete on 2007-08-27
Can I install that package while running off the LiveCD?

And if not can systemrescueCD write to NTFS?

P

---

### Post by steve.horsley on 2007-08-27
The instructions I linked you to for installing the ntfs-3g drivers don't say you have to reboot, so I guess you can install them on the live CD (in memory). Spooky, eh?

I haven't tried the system rescue CD - it might be worth a try. It's probably Linux based, so the mount and image commands you have already tried may work on that CD too.

---

### Post by southernman on 2007-08-27
> **steve.horsley said:**
> The instructions I linked you to for installing the ntfs-3g drivers don't say you have to reboot, so I guess you can install them on the live CD (in memory). Spooky, eh?

I haven't tried the system rescue CD - it might be worth a try. It's probably Linux based, so the mount and image commands you have already tried may work on that CD too.It is linux based... It works very well and has the already mentioned "testdisk" program installed which I used to retrieve nearly 20gb of data from a non-writeable (aka dead) ntfs harddrive of my brothers.

I thought maybe the OP would have at least taken the time to look into it, but you seem to have it under control steve. ;)

fwiw steve, you also may want to download that cd. It's very handy... kinda like knoppix. 

fwiw2, srcd also has a browser that will enable the op to use the cd (LIVECD) and tools on it... as well as search the internet for instructions on how to do things with it. again, it's a very handy tool to have in your cd wallet/toolbox.

---

### Post by steve.horsley on 2007-08-27
Can this rescue CD write to NTFS? I would guess the answer is yes because I guess it has to do that while "rescuing" hard drives, but it would be nice to see htat guess confirmed.

Actually, I feel I'm running our of ideas here - if he can't get NTFS writing enabled on the Ubuntu CD, I'm out of ideas. If it were me, I would try the rescue CD, but I would be exploring. I really just want to get this image made so it is possible to play around with the rescue CD without danger of making things worse.

---

### Post by ddrichardson on 2007-08-27
Yes it has [NTFS support]("http://www.sysresccd.org/Detailed-packages-list"). I can't recommend this disc enough, I've used it for ages.

---

### Post by skiwithpete on 2007-08-27
SystemRescueCD doesn't have a GUI so I can't use it, I'm not familiar enough with Linux, and I'd have to write down all the details in here.

Am going to try to get ntfs-3g to work now.  Will report back soon,

P

---

### Post by ddrichardson on 2007-08-27
System rescue disk does have a GUI - it uses Window Maker - you need to type startx for it to load. Gparted doesn't work without X.

---

### Post by vincentvee on 2007-08-27
how did it go?


> **skiwithpete said:**
> SystemRescueCD doesn't have a GUI so I can't use it, I'm not familiar enough with Linux, and I'd have to write down all the details in here.

Am going to try to get ntfs-3g to work now.  Will report back soon,

P

---

### Post by vincentvee on 2007-08-27
testdisk page [http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)
try that, it looks good

> **skiwithpete said:**
> I downloaded Ubuntu, and decided to use partition magic (in XP) to change the partition.  Part way through it failed, and now can't boot and just keeps going to BSOD and rebooting.  

The only thing that works is the LIVECD of Ubuntu I'm using now.

I can't mount the drive.


In details it says: 

 
Mount: wrong fs type, bad option, bad superblock on /dev/sda1  missing codepage or other error  In some cases info is found in syslog - try dmesg | tail or so.

I have no idea how to use Linux!!!  I'm lucky I got firefox to work.

Please help.  I can't lose all the stuff on C:  PLEASE.

P

---

### Post by skiwithpete on 2007-08-28
I am really having a tough time with SystemrescueCD.  Its gui is nothing like windows.  I can't get it to connect to the internet, and I can't seem to get it to image the hard drive - I tried to write to /dev/sda1/ and it wouldn't recognize it.  Then I tried /media/toshi250/ -which is what it was called when mounted in Ubuntu, and that didn't work either.

A little frustrated I thought I'd just try testdisk.  I did.  It saw that there were 2 partitions, I tried to make the first bootable again, and it didn't help windows load.  So I just turned it off - loaded back into Ubuntu, and here I am.

Oh yeah and I tried to get Ntfs-3g to work with the liveCD and it won't work - had an error message I can't recall - if it would help if I reposted it, let me know, and I'll replicate the error.

Thanks for your help.

I really need some next steps.  The more explicit the better.

Cheers,

p

---

### Post by steve.horsley on 2007-08-28
If therescue can write to ntfs it's worth trying to make an image with that. Get a root-privilege prompt (however that's done ) and use the command **fdisk -l ** (that's lower-case L for list) and see what drives there are. The rescue CD might call them hda/hdb instead of sda/sdb. Then try the mounting and imaging commands I gave earlier. 

I really can't help with using the reacue CD to fix your partition though. I've never used it.

---

### Post by skiwithpete on 2007-09-01
I've done it.

I backed up the HDD to an image using ntfs-3g.

I used test disk to retrieve individual files that are important - including honeymoon photos (honest guys I was in serious trouble if it hadn't worked).

I've saved all of the data.  I'm in the clear.

I wish I could hug you all.

The weirdest part is that I'll never know if I brush shoulders with you on the street - but thank you all.  I owe you my nuts (literally).

Thank you everyone.

Pete

---

### Post by southernman on 2007-09-01
> **skiwithpete said:**
> 

The weirdest part is that I'll never know if I brush shoulders with you on the street - but thank you all.  I owe you my nuts (literally).





Hey Pete, glad it worked out for you. 

Just one thing though. You don't own those anymore... your new wife does! 

:lolflag:

---

### Post by ddrichardson on 2007-09-01
My wife keeps mine in her purse - try looking there ;-)

---

### Post by vincentvee on 2007-09-02
good stuff, glad it worked out for you
also....about the nuts.......your just married?
you don't need them anymore, at least thats what my wife tells me....
lol

> **skiwithpete said:**
> I've done it.

I backed up the HDD to an image using ntfs-3g.

I used test disk to retrieve individual files that are important - including honeymoon photos (honest guys I was in serious trouble if it hadn't worked).

I've saved all of the data.  I'm in the clear.

I wish I could hug you all.

The weirdest part is that I'll never know if I brush shoulders with you on the street - but thank you all.  I owe you my nuts (literally).

Thank you everyone.

Pete

---

