---
title: "partition re-size post dual OS load???"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by buccaneere on 2007-11-09
Already got edgy eft loaded onto a vista box (single HDD), and want to decrease Vista's share, and increase Ubuntu's share.

All advice here seems to be about PRE-install partition re-sizing.

I prefer to not load any partition manager/re-sizing apps, if possible...

Thanks.

---

### Post by public_void on 2007-11-09
Try the GParted to resize partitions. It comes as a [liveCD]("http://gparted-livecd.tuxfamily.org/"), so you don't have to install any software.

---

### Post by buccaneere on 2007-11-09
> **public_void said:**
> Try the GParted to resize partitions. It comes as a [liveCD]("http://gparted-livecd.tuxfamily.org/"), so you don't have to install any software.


Thanks there void... 

I'm guessin' vista has no problem with it?

---

### Post by bulldog on 2007-11-09
Use Vista to shrink it's partition,not any thing else or your Vista is ruined.
Install your new linux in the free space you created,use the same swap.

---

### Post by Maestro23 on 2007-11-09
> **bulldog said:**
> Use Vista to shrink it's partition,not any thing else or your Vista is ruined.
Install your new linux in the free space you created,use the same swap.

Very much so.  Do all your housekeeping in Vista if you have critical data.  Or back that data up first and use Gparted like suggested.  If you are not familiar with Gparted... use Vista to resize its partiton.

---

### Post by buccaneere on 2007-11-09
Thanks there, bdog, m23, but ya' gotta read the title - POST dual OS load. I shoulda' said ***'after loading both OS's'***.

Sorry about that...

But alas, I'm readin' that vista 'disk space' is available for linux to copy files to. ??? This right?

So perhaps partition re-sizing isn't necessary? How do I see how much of the total HDD space is available to linux, for data to be written?

Thanks again there.

---

### Post by paulbeattie87 on 2007-11-09
I'd watch if your resizing the Ubuntu partition. I resized mine to give a XP partition a tad more space had to reinstall ubuntu as it wrecked the ext3 file system loaded up ubuntu and the number of errors was unreal told it to fix them all and in the end got a grub 15 error. Had to fixboot and fixmbr boot back into windows and then reinstall ubuntu which being linux doesn't take long :)

That was using paragon partition manager.

---

### Post by buccaneere on 2007-11-09
> **paulbeattie87 said:**
> I'd watch if your resizing the Ubuntu partition. I resized mine to give a XP partition a tad more space had to reinstall ubuntu as it wrecked the ext3 file system loaded up ubuntu and the number of errors was unreal told it to fix them all and in the end got a grub 15 error. Had to fixboot and fixmbr boot back into windows and then reinstall ubuntu which being linux doesn't take long :)

That was using paragon partition manager.

Yeah thanks there paul, but now I'm wonderin' if some info is correct - that vista 'disk space' is available for linux to copy files to. ??? This right?

If so, I don't really have the need to re-size...

Anybody?

---

### Post by bulldog on 2007-11-09
Yes it's possible to read and write to a NTFS file system.

look in synaptic for ntfs-3g package

---

### Post by buccaneere on 2007-11-09
> **bulldog said:**
> Yes it's possible to read and write to a NTFS file system.

look in synaptic for ntfs-3g package


Thanks bdog! That's good news.

Synaptic for ntfs 3g... that's linux' version of 'Disk x 'properties", like in windows?

---

### Post by Maestro23 on 2007-11-09
> **buccaneere said:**
> Thanks bdog! That's good news.

Synaptic for ntfs 3g... that's linux' version of 'Disk x 'properties", like in windows?

Synaptic GuI: System>>Admin>>Synaptic Package manager

Search for ntfs 3g.  It should be installed by default in Gutsy, so all you will need is** ntfs-config**.

Will put a menu entry under Apps>>Accessories>>System Tools

---

### Post by buccaneere on 2007-11-10
> **Maestro23 said:**
> Synaptic GuI: System>>Admin>>Synaptic Package manager

Search for ntfs 3g.  It should be installed by default in Gutsy, so all you will need is** ntfs-config**.

Will put a menu entry under Apps>>Accessories>>System Tools

I did not find package entitled ntfs 3g. 

Should it be available to extract from any of the following? (which I have at hand)

Ubuntu Edgy Eft live 
Winternals
Fedora 7 live
Fedora 7 full disc set
New Ubuntu
Tiny XP
PC linux OS

---

### Post by buccaneere on 2007-11-10
In addition, Disk Usage Analyzer shows file system capacity '37.6G'.
Gotta' increase that, without gettin' windows in a wad.

Easiest way? It's a 120G hdd, new/empty.

Thanks

---

### Post by buccaneere on 2007-11-10
> **buccaneere said:**
> In addition, Disk Usage Analyzer shows file system capacity '37.6G'.
[COLOR="Red"]Gotta' increase that, without gettin' windows in a wad.[/COLOR]

Easiest way? It's a 120G hdd, new/empty.

Thanks

> Quote:
Originally Posted by Maestro23  
Synaptic GuI: System>>Admin>>Synaptic Package manager

Search for ntfs 3g. It should be installed by default in Gutsy, so all you will need is ntfs-config.

Will put a menu entry under Apps>>Accessories>>System Tools 

I did not find package entitled ntfs 3g. 

[COLOR="Red"]Should it be available to extract from any of the following? (which I have at hand)[/COLOR]

Ubuntu Edgy Eft live 
Winternals
Fedora 7 live
Fedora 7 full disc set
New Ubuntu
Tiny XP
PC linux OS

bumpintodatop...

---

### Post by buccaneere on 2007-11-10
> **buccaneere said:**
> I did not find package entitled ntfs 3g. 

[COLOR="Red"]Should it be available to extract from any of the following? (which I have at hand)[/COLOR]

Ubuntu Edgy Eft live 
Winternals
Fedora 7 live
Fedora 7 full disc set
New Ubuntu
Tiny XP
PC linux OS

bumpintodatop...
bumpintodatopagain...

---

### Post by buccaneere on 2007-11-10
> **buccaneere said:**
> I did not find package entitled ntfs 3g. 

[COLOR="Red"]Should it be available to extract from any of the following? (which I have at hand)[/COLOR]

Ubuntu Edgy Eft live 
Winternals
Fedora 7 live
Fedora 7 full disc set
New Ubuntu
Tiny XP
PC linux OS

bumpintodatop...
In addition, Disk Usage Analyzer shows file system capacity '37.6G'.
Gotta' increase that, without gettin' windows in a wad.

Easiest way? It's a 120G hdd, new/empty.

Thanks

bumpintodatopagain...

---

