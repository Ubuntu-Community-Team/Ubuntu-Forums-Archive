---
title: "Ubuntu CD image too large for CD"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Fengrrl on 2007-10-05
I am trying to get off the launch pad installing Ubuntu on an old Windows 98 computer for my local Oxfam shop (it runs windows, but is riddled with viruses so I'm trying to get a fresh start).  I have downloaded a CD image ubuntu-6.06.1-desktop-i386.iso from a local mirror site but my CD write software says it is too large for the 700MB CD.  My laptop, which has the broadband connection, does not have a floppy drive and the ancient computer does not have a DVD reader, nor will it read memory sticks, so I think I'm stuck with CDs.  Is there a smaller CD image available that is suitable?

---

### Post by darren1270 on 2007-10-05
Just follow this link [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and burn the cd as an image.

you should have a .iso file where you save it.

---

### Post by armandh on 2007-10-05
I came to ubuntu after 7.04 which has always down loaded fine for me

---

### Post by Voland on 2007-10-05
> **Fengrrl said:**
>  I have downloaded a CD image ubuntu-6.06.1-desktop-i386.iso from a local mirror site but my CD write software says it is too large for the 700MB CD. 
Have you checked md5 sum? I think this image is corrupted, because I've made about 30 records of ubuntu-6.06.1-desktop-i386.iso CD image.

---

### Post by philinux on 2007-10-05
> **Fengrrl said:**
> I am trying to get off the launch pad installing Ubuntu on an old Windows 98 computer for my local Oxfam shop (it runs windows, but is riddled with viruses so I'm trying to get a fresh start).  I have downloaded a CD image ubuntu-6.06.1-desktop-i386.iso from a local mirror site but my CD write software says it is too large for the 700MB CD.  My laptop, which has the broadband connection, does not have a floppy drive and the ancient computer does not have a DVD reader, nor will it read memory sticks, so I think I'm stuck with CDs.  Is there a smaller CD image available that is suitable?

I'd get 7.04 too.

How much memory and hard disk space has the old 98er got.

---

### Post by Sef on 2007-10-05
> Have you checked md5 sum?

[How to MD5sum.]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by louieb on 2007-10-05
Perhaps your burning the .iso as a file. It needs to be burned as a disk image, (there is a difference). 
[BurningIsoHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BurningIsoHowto")
[Nuts on Getting Burning Booting Linux]("http://louboldt.com/ilinuxiso.htm")

---

### Post by anaconda on 2007-10-05
try this:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Those iso:s are less than 10MB each.

Some instructions in how to use these are here: 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

And some old CD-drives cant write bigger than 650MB CD:s  Even to a 700MB CD! But that would have to be quite old. from the time when there weren't any 700MB CD-r:s

---

### Post by Fengrrl on 2007-10-05
> **louieb said:**
> Perhaps your burning the .iso as a file. It needs to be burned as a disk image, (there is a difference). 
[BurningIsoHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BurningIsoHowto")
[Nuts on Getting Burning Booting Linux]("http://louboldt.com/ilinuxiso.htm")

I have checked the md5 sum, but I think I am trying to burn it as a file.  The Infrarecorder software recommended in the Ubuntu documentation didn't recognise my DVD drive, so I just tried to burn the disk using the software that came with my laptop which is NTI CD & DVD maker.  I told it I was trying to create a data CD.

---

### Post by Xyphus on 2007-10-05
You will definitely run into problems if you burn it as a standard data CD.  You will need to select burn ISO or burn Image in your CD software.  If you do not have that option, you may want to try either a trial version of something like Nero, or free CD Burning app like CDBurnerXP if running under Windows.

CDBurnerXP can be found at [http://cdburnerxp.se/](http://cdburnerxp.se/) and it will burn ISO images.

---

### Post by dptxp on 2007-10-05
There is burncdcc for Windows.
Whatever you use, use 'burn image' command.
Keep speed as 'AUTO', no need for low speeds.

---

### Post by Fengrrl on 2007-10-05
It has 262Mb of memory and 212Mb on hard drive, with 17.5Mb free

---

### Post by Fengrrl on 2007-10-05
thank you all for your help. I managed to burn an image using CDBurnerXP, but the old computer still won't boot from the CD.  I have set the bios to look at the CD drive first.

---

### Post by desertboy on 2007-10-05
Not sure why it won't boot but I don't think the livecd's run with less than 512meg of ram (Except for xubuntu)

---

### Post by louieb on 2007-10-05
> **desertboy said:**
> Not sure why it won't boot but I don't think the livecd's run with less than 512meg of ram (Except for xubuntu)

256MB is marginal  for the live CD but if you burned it right you should get the first menu before it hangs up. (look at the CD in windows explorer if you see a bunch of files and folders then you got it burned right).  

> **dptxp said:**
> There is burncdcc for Windows.
Whatever you use, use 'burn image' command.
Keep speed as 'AUTO', no need for low speeds.

That hasn't been my experience. The faster I burn an ISO the greater the chance I've just created a coaster. Great  for drinks but lousy as a bootable CD. It just doesn't take that long to burn it at 2x or 4x.
> It has 262Mb of memory and 212Mb on hard drive, with 17.5Mb free

May give windows a problem if you try to shrink its partition. Your about 90% full now. Bet it runs slowly. NTFS start slowing down at 75%. Really don't thing I'd try to install Ubuntu on that drive.

---

### Post by dptxp on 2007-10-08
Ubuntu Live CD shall not run with 256 MB ram, but you get the first screen.
Make a SWAP partition of 512 MB to 1 GB with GParted first.
Then you can run and install regular Ubuntu. Speed will be OK after installation.

With 256 MB RAM (and no SWAP) you can run/install Xubuntu (add gnome later) or you can use alternate CD.

But you iso has to be OK and you have to burn using 'burn image' command.

You need 6 GB (min 4 GB) disc space for Ubuntu ( root).

---

### Post by GerryB on 2007-10-08
> **Fengrrl said:**
> thank you all for your help. I managed to burn an image using CDBurnerXP, but the old computer still won't boot from the CD.  I have set the bios to look at the CD drive first.

I'm running Ubuntu 7.04 (Feisty Fawn) on a 440 Mhz computer with 320 MB of RAM and a 10 MB hard drive - no problems. I've run across computers that won't boot from the CD drive even after changing the booting sequence in the BIOS. Older Compaq computers are among them. I've never solved that problem but maybe an expert on BIOS's on this forum could come to our rescue. Another idea: download Puppy Linux and burn it to CD with BurnCDCC (it can only burn images). This small distro which is either 45 MB or 70 MB depending on the version will tell you if the problem is the CD size or your BIOS. Good luck!

---

