---
title: "Journaled FS supported by Mac, Linux, and Windows?"
date: 2008-10-16
forum: Apple Hardware Users
---

### Post by enigma_0Z on 2008-10-16
A little history. I'm dealing with a support issue with Dell. While my laptop has been out, however, I decided to pick up a SATA/IDE -> USB adapter to get my stuff off my removed laptop hdd. The one I got was faulty (the power brick actually exploded in my hand) so I took it back and bought a different brand. The first one was some no name brand, the second was "cool max" but I'm not sure if this is a no-namer too... Anyway I digress.

In light of this situation, I'm looking into purchasing a WD 1 TB My Book as an upgrade to replace my current 80 GB IDE drive in a no-name enclosure, being afraid of the failure rate of no-name hardware...

Anyways, so I'm looking for what kind of filesystem I can put on the disk so that it is accessable from Linux first and foremost, and Windows/OSX tied for second. I know that FAT32 and EXT2 will both work, but I'd *like* a journaled FS for a bit of added stability and reliability with such a large drive and investment...

So, are there any that are three-way cross compatible? If we only have two-ways, I need need linux compatibility...

Thanks.

---

### Post by cyberdork33 on 2008-10-16
none.

FAT32 is most compatible between all three, then NTFS, then HFS+ (unjournaled).

---

### Post by jerome1232 on 2008-10-16
That being said all of them can be configured to work with NTFS. I understand you have to change something so that macs can write to an NTFS drive but there you have it.

edit: I don't know how reliable Mac's are with ntfs so you might want to research that a bit.

edit: Some looking around shows Mac's can use ntfs-3g (that's what Linux uses to read/write to ntfs volumes)

---

### Post by cyberdork33 on 2008-10-16
> **jerome1232 said:**
> That being said all of them can be configured to work with NTFS. I understand you have to change something so that macs can write to an NTFS drive but there you have it.

yes, you have to use MacFUSE.

---

### Post by enigma_0Z on 2008-10-16
Call me a bit jaded, but I don't particularly trust NTFS because MS makes it...

Is there a HFS+ driver for XP/Vista?

I know there's an EXT2 driver for Mac, is there one for XP/Vista? Is there any reliability issues w/ using EXT2 for a backup volume? Is there any reliability issues w/ EXT2 for Mac and/or Vista?

---

### Post by jerome1232 on 2008-10-16
NTFS is the only journaled file system the works across all three OS's. And I trust it over fat it's actually a decent file system.

ext2 isn't journaled. Although Linux/Mac can use ext3, Windows will use it as ext2
fat fragments easily and isn't journaled.
Linux can't write to a hfs+j partition, the journal must be removed for read and write access (making it hfs+, not journaled). (it can read from a hfs+j partition though) Windows can access a hfs+j partition but the software costs 40 bucks from what I can see.

---

### Post by enigma_0Z on 2008-10-17
> **jerome1232 said:**
> NTFS is the only journaled file system the works across all three OS's. And I trust it over fat it's actually a decent file system.

ext2 isn't journaled. Although Linux/Mac can use ext3, Windows will use it as ext2
fat fragments easily and isn't journaled.
Linux can't write to a hfs+j partition, the journal must be removed for read and write access (making it hfs+, not journaled). (it can read from a hfs+j partition though) Windows can access a hfs+j partition but the software costs 40 bucks from what I can see.

I thought so about ext2/3, and I knew that about FAT. Of the fs's, I trust FAT the least, by the way. Don't really want to pay $40 for windows hfs+j support if it doesn't come with linux support too, and read-only is not an option.

What's the NTFS support like on Mac and Linux. I'm using this for a backup device, so how *reliable* and *fast* is NTFS access from a Mac or a Linux box? Is there a fsck.ntfs that *works* for Mac and Linux?

---

### Post by jerome1232 on 2008-10-17
Well, using the ntfs-3g driver under linux I haven't had any corruption from writing to an ntfs drive, you can get a suite of tools from the repos ntfsprogs, comes with ntfsfix, but it seems to be only able to do basic fixes, like remove the unclean shutdown flag so you can mount it (if say Windows crashed and you never booted back into Windows). From helping people on the forums if your using ntfs and if it corrupts somehow, your going to need Windows to do the repairs. (But if your not using Windows there's no reason to use ntfs)

There's no tool that will replace Windows chkdsk.

It looks like good hfs+ support is coming to Linux [http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/) (I can't seem to figure out how to refer to the filesystem correctly lol, it looks like hfs+ is journaled but you can disable that with a Mac and then Linux can read/write to it just fine.)

---

### Post by Steveway on 2008-10-17
How about setting up a server (a cheap 200MHZ thing is enough) connect the Harddrive to it and format it with whatever you want and then set up NFS.
I do it that way and it's fast enough for me.

---

### Post by cyberdork33 on 2008-10-17
> **jerome1232 said:**
> Well, using the ntfs-3g driver under linux I haven't had any corruption from writing to an ntfs drive, you can get a suite of tools from the repos ntfsprogs, comes with ntfsfix, but it seems to be only able to do basic fixes, like remove the unclean shutdown flag so you can mount it (if say Windows crashed and you never booted back into Windows).  It is essentially the same driver code you use in OS X. Userspace filesystem drivers are a little slower than native, but it works well from all three systems and that is a plus.

> **jerome1232 said:**
> It looks like good hfs+ support is coming to Linux [http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/) (I can't seem to figure out how to refer to the filesystem correctly lol, it looks like hfs+ is journaled but you can disable that with a Mac and then Linux can read/write to it just fine.)
Yes, HFS+ can be journaled or non-journaled. Disabling journalling though, please much disables anything that is actually attractive about using it in non-Apple OSs.

> **Steveway said:**
> How about setting up a server (a cheap 200MHZ thing is enough) connect the Harddrive to it and format it with whatever you want and then set up NFS. I do it that way and it's fast enough for me.
Network shares are the easiest way to share with all OSs and all machines too...

---

### Post by jerome1232 on 2008-10-17
> **Steveway said:**
> How about setting up a server (a cheap 200MHZ thing is enough) connect the Harddrive to it and format it with whatever you want and then set up NFS.
I do it that way and it's fast enough for me.

> **cyberdork33 said:**
> Network shares are the easiest way to share with all OSs and all machines too...

I believe you guys are very correct, a file server is a far superior solution, as long as these computers are all on the same LAN. Using rsync speed shouldn't be an issue after the first round of backups have been done.

---

### Post by enigma_0Z on 2008-10-17
> **jerome1232 said:**
> I believe you guys are very correct, a file server is a far superior solution, as long as these computers are all on the same LAN. Using rsync speed shouldn't be an issue after the first round of backups have been done.

At my old worplace, we used a Mini ITX VIA board for some of our dumb-terminal rdesktop workstations... Would such a system work? And can I get some recommendations on hardware to build such a NAS backup system??

One of the things that I did with my backups is I compressed them to save space on the disk. Is there a solution that combines the robustness of rsync with compression?

---

### Post by cyberdork33 on 2008-10-17
> **enigma_0Z said:**
> At my old worplace, we used a Mini ITX VIA board for some of our dumb-terminal rdesktop workstations... Would such a system work? And can I get some recommendations on hardware to build such a NAS backup system??

One of the things that I did with my backups is I compressed them to save space on the disk. Is there a solution that combines the robustness of rsync with compression?

I think the best solution is to get a router with a USB port or integrated Storage (Think like the Time Capsule) Linksys has similar products. Of course then you are limited to the filesystems that the router can use... 

I personally have a Windows machine (I know, I know) acting as a DVR / Media /File server. Just using a samba share. File servers are pretty easy to build though, you can use pretty old hardware since the performance demands are not that high (if you have a limited number of users). An old laptop with Ubuntu server on it would work great since it is compact, and most laptops have extra power-saving features. You can also use a network share for Time Machine backups if you plan to do that for OSX.

---

### Post by jerome1232 on 2008-10-17
As far as the compression you were asking about, one thing I thought is nice about the NTFS filesystem is it can do on the fly transparent compression.  Any file that is written to the 'compressed' folder is compressed using the LZ77 algorithm, same algorithm used for zip files.

As to whether this feature works under ntfs-3g I'm uncertain.

From good old wikipedia here's a list of filesystems that support on the fly compression, it may be dated I don't know but good info none-the-less.

edit: forgot the link lol [http://en.wikipedia.org/wiki/Category:Compression_file_systems](http://en.wikipedia.org/wiki/Category:Compression_file_systems)

A project I thought was interesting (Linux) [http://www.linux.com/feature/137234](http://www.linux.com/feature/137234)

makes a fuse filesystem that is transparent, compressed, and will write to any filesystem the linux kernel supports. It can even intelligently decide if it's worth the processor time vs saved space to compress a file (like mp3's, jpegs, are already compressed and won't compress much further, sometimes they even bulk up)

another edit: Adding this type of stuff starts to task the processor, so if used you may need something more than 400 MHZ.

My last edit I promise: While looking at some info for something entierly unrelated, found that ntfs-3g does not support that cool transparent, on-the-fly compression and encryption with ntfs that I was talking about. Although it would work via that compfused project.

---

### Post by enigma_0Z on 2008-10-20
Hmm... While some NAS (Network Attached Storage) rsync-based backup system may be better from an interoperability standpoint, I'm still seeing a couple of disadvantages compared to a simple USB disk:

1. Slightly less security - you can access the NAS device over the network, the USB device needs to be plugged in to be accessed...
2. Much less thoroughput - I've got gigs of data that I want to back up, and if I'm on the network, a full backup will take quite a bit more time.
3. Portability - If I need to move the files between computers, I simply unplug the disk and move it to another computer... with a NAS device, would it be feasible to use a USB disk connected to the NAS server?
4. Interoperability - If I need to restore files and I don't have the home-built NAS device available, how would I access my files (see #3 too)

---

