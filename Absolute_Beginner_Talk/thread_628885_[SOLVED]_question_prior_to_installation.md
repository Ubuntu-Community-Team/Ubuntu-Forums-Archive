---
title: "[SOLVED] question prior to installation"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-12-01
I've been around here a lot, and I've been playing with Linux a lot, although I don't know much. I have taken Linux off my system and I want to install it again. Here's what's available on my system. I want to make the best choice for the most successful installation. 

Hard Disk 1 250 Gig. Western Digital IDE. Formatted NTFS I have Windows XP installed, and most of my games 76 Gig left.

Hard Disk 2 200 Gig (windows reports it at 186.?? gig) Formatted NTFS nothing on it right now. Would probably use it for my music collection, which would probably consume this whole disc and more.

Hard Disk 3 External, connected via Firewire - Western Digital - 'My Book' - 750 gig -- Formatted Fat 32 -- 616 Gig left.

I am forever, fooling around with different Distros here and there.

Need a quick suggestion on where to put Ubuntu. I am thinking about putting it on the same disk as Windows. If I let Ubuntu use the remaining disk space for it's installation, will I need to reformat or repartition my other drive? Or can I use Ubuntu to rip my CD's to my other drives and allow Windows to read from these disks as well as Ubuntu?

Also, how much difference is there in Feisty Fawn and Gutsy Gibbon?

---

### Post by red_Marvin on 2007-12-01
76G is more than enough for a standard ubuntu install, my root partition only uses 14G at the moment so that should not be a problem.

You should be able to rip to the second hdd, however ntfs is a closed format, so there *may* be problems, and it's not enabled out of the box -so you need to do some googling or forum searching to make it work.

Another route might be to format the second hdd to ext2/3 and then install ext windows drivers.

As for differences between fiesty and gutsy, compiz fusion is installed and enabled by default. I guess hardware support has improved too (since it's a later release).

---

### Post by dcallman49 on 2007-12-01
I agree ubuntu does not need that much on its own, I would split the 76gig between ubuntu and a seperate partition for home.  

I have had no problems writing to NTFS partitions using Feisty or Gutsy myself.

Good Luck:KS

---

### Post by bgast1 on 2007-12-01
Thanks very much for the reply. I have a program that can let me repartition and reformat that second drive to FAT 32 really quick and easy. Will that help me? I like that 2nd option too of installing Linux on that drive. 

Here's what is keeping me from switching to Linux 100%. I really wish I could. My sound card is a Creative X-Fi Extreme Gamers card and there just is no support for it at all in 32 bit. I've heard of people who know a lot about ALSA and other drivers tweaking them and getting Creative stuff to work, but I don't have that kind of knowledge, yet anyway. My onboard sound works fine with Linux.

Also, the gaming support. Although I am going to try to get Doom 3 working. I've heard of people using Parallels to play Command & Conquer 3 Tiberium Wars, but I just haven't gotten that far yet, as far as running a virtual system. Some folks have said that they don't work so well for games. Hence, my desire to dual boot. 

Sounds like other than Compiz, I wouldn't know the difference between Feisty Fawn and Gutsy Gibbon. I have both, so I will install the Gutsy Gibbon.

---

### Post by bgast1 on 2007-12-01
This is turning into a much bigger project, because I want to do it right and don't want to screw up my Windows installation. My wife needs it, and I need it for games. 

I have a partitioning program. I want to allocate about 25 gig for Linux.  My choices for partitioning are:
FAT 32, NTFS, Ext2, Ext3, ReiserFS, Linux Swap, none. 

How do I go about this? I wasn't comfortable using what comes on the Gutsy Gibbon CD that I downloaded.

---

### Post by dcallman49 on 2007-12-01
Use Ext 3, I would recommend following a guide.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

I dual boot to XP on my Dell 1501 Laptop.  I have ran a VMWARE workstation converted image of my XP system inside Ubuntu a little bit, but I will keep dual boot as well.

On my laptop I have. 120GB partitioned XP = 45, ubuntu=30, and about 35 for Fat32, Dell also had a restore partition I left there as well.

Having other hard disks give you many choices.  With my laptop I had to make do with what was given.

Good luck.

---

### Post by bgast1 on 2007-12-01
Having 3 hard drives makes decisions a little tougher. The installer wants to initially install on my 750 gig external hard drive. But I am not sure how it will go about partitioning it, so that seems out. I have installed on my 200 gig hard drive without problems, and have ripped my CD's to that drive as well, but then Windows cannot see those files should I want to play them in Windows. If I try to to rip them to my large external hard drive, then I have a lot of wasted hard drive space on my Linux installation. 

I think some of the other distros give you the option of using the free space on your windows installation, but I did not see that here.

---

### Post by dcallman49 on 2007-12-01
It has that option, but I usually use GParted LiveCD.  And you do need a ubuntu root drive and a swap partition.

Have fun

---

### Post by bgast1 on 2007-12-01
Finally ended up installing to my second hard drive. I can always go back to my partitioning program and resize the partitions on my disk. It is Acronis Disk Director Suite. It has made my life easier more times than I can count. I was told once, that I didn't need it or anything else like it, but I don't know where I would have been without it. Still needed Windows 98 to fix my mbr once or twice though.

Oh by the way, Since I am going to be using it, What kind of partition should I make the remainder of the hard disk that Linux is on, to be able to read and write both Linux and Windows. I will mainly be ripping my CD's to the drive, will ripping them in FLAC make any difference? I want to have the option to listen to music both in Windows and LInux.

---

### Post by overdrank on 2007-12-01
> **bgast1 said:**
> Finally ended up installing to my second hard drive. I can always go back to my partitioning program and resize the partitions on my disk. It is Acronis Disk Director Suite. It has made my life easier more times than I can count. I was told once, that I didn't need it or anything else like it, but I don't know where I would have been without it. Still needed Windows 98 to fix my mbr once or twice though.

Oh by the way, Since I am going to be using it, What kind of partition should I make the remainder of the hard disk that Linux is on, to be able to read and write both Linux and Windows. I will mainly be ripping my CD's to the drive, will ripping them in FLAC make any difference? I want to have the option to listen to music both in Windows and LInux.

Hi and I usually use the Fat 32 file system to share between them but that is my opinion. :)

---

### Post by bgast1 on 2007-12-02
Looks like I got this solved. I made my Linux partition 30 gig. Tried to increase my swap file size but it wouldn't let me. 

Linux sees my external hard drive. For type is says vfat. Why?

Linux does not see my windows hard drive or the new fat 32 partition that I just created. 

Please not that I got this information from 'System Monitor' and not looking anywhere else. I suspect that it will see them if I go looking for them under 'Places'

---

