---
title: "Sharing a partition between WinXP and Ubuntu"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by entic on 2005-07-19
I am BRAND NEW to Ubuntu and Linux... my first install ever, so please try not to be too technical with your responses. I Have the following setup:

160GB HDD split into:

~26GB NTFS with Windows XP installed on it
~26GB ext3 with Ubuntu installed on it
~106GB NTFS
~1.5GB Swap (Does Ubuntu only use this Swap, or does WinXP use it too?)

I don't have any qualms with reformatting or completely changing what I have as I just moved from a 120GB HDD and still have all my data and another windows install on it. My goal is to have a dual boot between WinXP and Ubuntu, and use the remaining space as a storage area to be shared between the two OS (movies, mp3s, documents, pictures). I don't know how large I'd need the WinXP and Ubuntu partitions to be... I don't intend to install many games or large software, so I might make them smaller (10GB each? Smaller?) and use the rest for the shared space.

So, what should I do to achieve this goal? Is NTFS a good file system for the shared space? I'm having a hard time accessing files from other hard drives in Ubuntu, and I don't know if that's because they're in NTFS or because I'm doing something wrong. In the dev folder, hda1-5 and hdb1-5 have red X's as icons. I really am lost... thanks in advance for any help you can give. I'm looking forward to giving Ubuntu a shot!

---

### Post by Kyral on 2005-07-19
FAT32 is the best for a shared space. Linux cannot write to NTFS partitions, but can read/write to FAT32

---

### Post by aysiu on 2005-07-19
[QUOTE=entic]
~26GB NTFS with Windows XP installed on it
~26GB ext3 with Ubuntu installed on it
~106GB NTFS
~1.5GB Swap (Does Ubuntu only use this Swap, or does WinXP use it too?)
[/QUOTE] I think your current scheme is fine. The only thing you have to do is reformat the 106 GB partition as FAT32 instead of NTFS. Then, both XP and Ubuntu will be able to read from and write to it.

After the reformat, you might want to follow the steps here
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by davidgypsy on 2005-07-20
I have a small seperate HD formatted to fat32 just for sharing files between the two. Works great!

---

### Post by maruchan on 2005-07-20
While you're in partitioning mode, you should know that some people make a separate "home" partition for their Linux documents (and sometimes even a separate partition for installing specific software) so it's easy to change distros if necessary.

---

### Post by entic on 2005-07-20
A few things:

Won't Fat32 be painfully slow for large files?
I don't exactly understand the point of a home partition... what would one put there? Do installed programs go there?

Last question, but different topic:

Is it possible to have Thunderbird on both WinXP and Ubuntu share the same personal mail folders, settings, etc?

---

### Post by maruchan on 2005-07-20
Home Partition = "My Documents" :)

> Is it possible to have Thunderbird on both WinXP and Ubuntu share the same personal mail folders, settings, etc?

Well, there's a reason to have a FAT32 partition if I've ever heard one.

---

### Post by aysiu on 2005-07-20
[QUOTE=entic]A few things:
Won't Fat32 be painfully slow for large files?[/quote] I haven't noticed that much of a difference.

> 
I don't exactly understand the point of a home partition... what would one put there? Do installed programs go there? /home is where all your settings go. Theoretically, it's also where your files go, but if you're using a shared FAT32 to store files, the FAT partition is probably where your files will go. Do you know C:\Documents and Settings\Username\Application Data? That stuff is all in the /home partition. In both Windows and Linux, this data is all stored in hidden folders.

> 
Is it possible to have Thunderbird on both WinXP and Ubuntu share the same personal mail folders, settings, etc? No. As I said before, Windows stores settings in C:\Documents and Settings\Username\Application Data. Linux stores settings in /home/username

---

### Post by entic on 2005-07-20
[QUOTE=aysiu]I haven't noticed that much of a difference.

 /home is where all your settings go. Theoretically, it's also where your files go, but if you're using a shared FAT32 to store files, the FAT partition is probably where your files will go. Do you know C:\Documents and Settings\Username\Application Data? That stuff is all in the /home partition. In both Windows and Linux, this data is all stored in hidden folders.

 No. As I said before, Windows stores settings in C:\Documents and Settings\Username\Application Data. Linux stores settings in /home/username[/QUOTE]
 Thanks alot, guys. I guess I will do the FAT32 Partition and maybe make it a bit bigger... like, 130gb, and then have a 15gb WinXP partition in NTFS, a 5gb /root, and a 15gb /home.

As for the thunderbird, I'm pretty sure the settings can be altered (at least in the Windows version) to change the location of the Personal Folders. If this is the case, and assuming the mail and settings files are in the same format in both the Windows and Linux versions (which I think they are, according to Mozilla), couldn't I set the location for both Windows and Linux programs to be the same spot on the FAT32 partition?

---

### Post by aysiu on 2005-07-20
These two links may help:
[http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location)
[http://www.worldstart.com/tips/tips.php/1644](http://www.worldstart.com/tips/tips.php/1644)

---

### Post by FLeiXiuS on 2005-07-20
Hmm, I've always loved using a Native Linux partition.  Linux to me has seemed to break my partition tables after so many writes / reads.  The way I'd go about doing it is using ext3 and installing Explore2fs on the windows drive.  This will enable windows to read/write to ext2/ext3.  

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)


Check it out  ;-)

---

### Post by entic on 2005-07-20
[QUOTE=FLeiXiuS]Hmm, I've always loved using a Native Linux partition.  Linux to me has seemed to break my partition tables after so many writes / reads.  The way I'd go about doing it is using ext3 and installing Explore2fs on the windows drive.  This will enable windows to read/write to ext2/ext3.  

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)


Check it out  ;-)[/QUOTE]
 Fleixius--at that site, the author writes "The exception to this is EXT3 which is compatible.  Writing to EXT3 is not supported." Wouldn't that mean I'd have to go with ext2, which is much slower according to what I've read.

Also, would using this program enable me to use the ext2/ext3 partition in windows as if I was using any old NTFS partition? Or would I have to write files to it/read it from a special application? Would that preclude me from, say, downloading to it using BitTorrent, or storing mp3s on it and playing them using Winamp (or whatever)?

---

### Post by entic on 2005-07-21
Alright, I haven't yet done the repartitioning everything... I am actually reconsidering using Ubuntu or Linux in general because after using it all day I feel like, though it is more consistent (IE, you run a file in Ubuntu and it WILL OPEN without pussyfooting, unlike WinXP often does), it seems MUCH slower (subjectively noticed mostly from browsing w/ FireFox, playing CDs and DVDs). I am not willing to give up so soon, especially with all the great help I've received, but am I doing something wrong maybe? It just seems far, far slower than I'm used to. I rebooted into Windows a few times to be sure, and I am pretty sure. But, then again, Windows is running much faster since I turned off auto-update and no longer use the common Bloatware (TM) and stick to stuff FireFox and Thunderbird for internet, AntiVir and the hardware firewall on my router for security, OpenOffice for working, VLC Media Player for video, etc etc.

---

### Post by aysiu on 2005-07-21
[QUOTE=entic]Alright, I haven't yet done the repartitioning everything... I am actually reconsidering using Ubuntu or Linux in general because after using it all day I feel like, though it is more consistent (IE, you run a file in Ubuntu and it WILL OPEN without pussyfooting, unlike WinXP often does), it seems MUCH slower (subjectively noticed mostly from browsing w/ FireFox, playing CDs and DVDs). [/QUOTE] Have you already installed Ubuntu? If you're running the live CD, it's supposed to be slower, as it's running completely off RAM instead of the hard drive. Once you install Ubuntu, it should be much faster. Try running Windows XP completely off RAM...

---

### Post by entic on 2005-07-21
No, no... it's installed and everything. I'm on WinXP at the moment and it really feels much faster in terms of web browsing, load times, and switching from program to program.

---

### Post by drigloi on 2005-07-28
Some thoughts about sharing a partition between Win and Linux:

1. good old FAT32 is good enough for 30-40 GB sized partitions, bigger ones will be slow and FAT32 fragments easily too
2. you can teach Linux to write to NTFS by using ntfs.sys - however this emulation is really sloooowwwww (believe me 45-50 kilobytes/sec)
3. you can teach Windows (XP SP2 too) to read/write ext2 filesystems as if they were native Windows filesystems (you can access them through drive letters and read/write to them, even install software on them). You can read a howto about this here: [http://xpedition.mine.nu/eng/about.html#ext2fsd](http://xpedition.mine.nu/eng/about.html#ext2fsd)

Ext2Fsd 0.24 features:
- stable ext2 read/write and ext3 read (plus experimental write)
- support for UTF8 encoding (must be set through regedit)
- access is fast (20-25 MB/s)
- SP2 compatibility
- and yes it's GPLed

I personally use this this driver on multiple computers without any problems.

Note:
- you should use ext2 for stability (and no, ext2 is not a slow filesystem, actually it is more fast then ext3 - btw ext3 is just ext2 plus journal) - you can easily make ext3 to ext2 without affecting your data (do a google :)
- you should make your ext2 filesystem's partition an NTFS/HPFS typed partition (07). You can do this with eg. cfdisk. Changing just the partition type won't destroy the data on your partition. If your ext2 is on an NTFS partition Windows will handle it transparently (if it is a 82 type Linux partition, WIndows will still handle it but will not register it in the registry and some apps like MSInstaller won't work on such volumes)
- ext2 is far better than FAT32 because it can be of any size without performance issues and won't fragment with time

---

### Post by sooqing on 2005-07-28
[QUOTE=entic]~1.5GB Swap (Does Ubuntu only use this Swap, or does WinXP use it too?[/QUOTE]

Think u can configure Windows and Linux to share the same swap..

---

