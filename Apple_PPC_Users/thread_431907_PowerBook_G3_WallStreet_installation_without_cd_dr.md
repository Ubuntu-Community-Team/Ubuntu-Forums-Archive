---
title: "PowerBook G3 WallStreet installation without cd drive"
date: 2007-05-03
forum: Apple PPC Users
---

### Post by hi-0ctane on 2007-05-03
Hello, my first post.

I have a PowerBook G3 WallStreet 233Mhz 160MB RAM 2GB HD and I want to install Ubuntu Linux for PPC
I have Mac OS 9 installed

But I don´t have cd-rom drive to load iso boot install.

What do I have:
* Floppy drive 1.44MB
* USB PCMCIA Card working, it reads my 1GB pen-drive.
* 1.5GB Free on Hard Disk

Can I install ubuntu linux? Oh, btw:
* I don´t have internet access to install ubuntu, because some important files have been deleted (ok, I did it) so, internet is not working

---

### Post by stmiller on 2007-05-03
Is this an old-world machine? If so, you'll need an OS 9 disc to create a proper partition. And that would require a local CD drive. Search the forum or google for BootX for more details.

---

### Post by hi-0ctane on 2007-05-03
> **stmiller said:**
> Is this an old-world machine? If so, you'll need an OS 9 disc to create a proper partition. And that would require a local CD drive. Search the forum or google for BootX for more details.

Yeah..It´s and oldworld machine

I don´t have the cd-drive and I don´t have Mac OS 9 CD :(
So, I really need to buy both? (not so bad, I know where I can find it)

What BootX can do?
--------
EDIT:  BootX not necessary, I don´t want to run Mac OS 9 anymore, I want to replace Mac OS 9 with Ubuntu Linux.

I want to use Ubuntu Linux ONLY

---

### Post by hi-0ctane on 2007-05-04
Pls, do I have another option? :(

---

### Post by john8520 on 2007-05-04
Yes, you do. Wallstreets have HDI-30 SCSI ports, so you can buy an HDI-30 to 25pin SCSI adapter, then pick up a SCSI CD drive (both these items can be had pretty cheap). 

For old world machines, such as the wallstreet, pdq, beige G3, etc. you *have* to install OS 8/9 on it. This is because yaboot (what is required to either use linux standalone, or dual boot linux and OS X on a new world mac) will not install on a wallstreet/pdq/beige because their openfirmware isn't new enough.

I've done it before, getting linux on an old world mac (I own a PDQ and two beige G3s) is **not** an easy task like it is on a newworld mac. This isn't to say you shouldn't try it, but if you do, be prepared for a challenge.

---

### Post by stmiller on 2007-05-04
The mac OS 9 cd is available on most popular torrent search sites, if you are desperate.

G4 TiBooks are going for $200-$300 on craigslist.org (Not sure if you are in the US?) if you want an alternative...

---

### Post by hi-0ctane on 2007-05-05
> **john8520 said:**
> Yes, you do. Wallstreets have HDI-30 SCSI ports, so you can buy an HDI-30 to 25pin SCSI adapter, then pick up a SCSI CD drive (both these items can be had pretty cheap). 

For old world machines, such as the wallstreet, pdq, beige G3, etc. you *have* to install OS 8/9 on it. This is because yaboot (what is required to either use linux standalone, or dual boot linux and OS X on a new world mac) will not install on a wallstreet/pdq/beige because their openfirmware isn't new enough.

I've done it before, getting linux on an old world mac (I own a PDQ and two beige G3s) is **not** an easy task like it is on a newworld mac. This isn't to say you shouldn't try it, but if you do, be prepared for a challenge.

This is a very good idea.
Can I boot from a HDI-30 SCSI using CD-ROM ou Hard Disk drive ?

---

### Post by Tommy on 2007-06-01
> **hi-0ctane said:**
> This is a very good idea.
Can I boot from a HDI-30 SCSI using CD-ROM ou Hard Disk drive ?

Yes, as long as it's a device recognized by the Mac. Any SCSI CD-ROM that was originally marketed for a Mac will work. I'm mentioning it because you might turn up an external SCSI drive made for a SUN workstation or something, and while it might work, it might not.

Note, however, that you STILL need an OS-9 disk (CD or hard drive) to boot. You can boot from the OS-9 CD (or an OS-8 CD if your hardware is old enough).

---

