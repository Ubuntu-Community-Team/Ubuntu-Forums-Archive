---
title: "Grub"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by pe1800 on 2007-03-10
HDA with WXP, HDB with Ubuntu 6.10

Please advise, how can I create a floppy, as a safeguard to retain my ability to, at all times, boot into either WXP or Ubuntu?

I appreciate your help.

pe1800
:)

---

### Post by Crooksey on 2007-03-10
```
 man grub
```

..but i doubt your MBR will suddenly stop working...

---

### Post by pe1800 on 2007-03-10
Thank you, but this means nothing to me. I am a novice! Those man pages are written in such a way that nobody can understand it.I would like to create a floppy which, in an emergency, will let me boot into Ubuntu or WXP, as required.

---

### Post by confused57 on 2007-03-10
Maybe this will work:
[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

Is grub installed to your Windows mbr?

Check out this site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Great info on grub, check out GAG & Super Grub Disk in the index.

---

### Post by torgrot on 2007-03-10
Download GAG and create a boot floppy.  I have had some problems with my GRUB installation but GAG has always booted my windows disk.  

torgrot

---

### Post by rusty4r on 2007-03-10
Grub is a wonderful thing. Herman's grub page that confused57 pointed you to will show you how.

---

### Post by confused57 on 2007-03-10
Here's is a subsection of the Hermanzone site I linked you to:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
part of the way down the page there is a index link to creating a cd-rw boot cd or a grub floppy...maybe this will work.

Also, you might want to check out the Super Grub Disk, it can boot Windows or Linux or restore Windows code or grub to your mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only approx. 500 kb to download, but it might come in hand for booting your system

I saw you posted in the "howto" written by catlett...he hasn't been active in the forums for several months, but you'll get excellent support & suggestions here.

---

### Post by pe1800 on 2007-03-10
> **torgrot said:**
> Download GAG and create a boot floppy.  I have had some problems with my GRUB installation but GAG has always booted my windows disk.  

torgrot

Thank you! Yes, I think I remember I have heard of GAG.

---

### Post by pe1800 on 2007-03-10
> **confused57 said:**
> Here's is a subsection of the Hermanzone site I linked you to:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
part of the way down the page there is a index link to creating a cd-rw boot cd or a grub floppy...maybe this will work.

Also, you might want to check out the Super Grub Disk, it can boot Windows or Linux or restore Windows code or grub to your mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only approx. 500 kb to download, but it might come in hand for booting your system

I saw you posted in the "howto" written by catlett...he hasn't been active in the forums for several months, but you'll get excellent support & suggestions here.

Thank you! I will study that GRUB page.

---

### Post by pe1800 on 2007-03-11
I created a GRUB floppy, then booted with the floppy in the drive. I pressed "C". Then used the GRUB command prompt to boot into WXP. It worked!

I wonder though, was that the floppy or the GRUB on the hard drive. How do I know whether the floppy would work when there is no GRUB on the hard drive or when it is damaged?

Thank you!

---

### Post by torgrot on 2007-03-11
I am not sure about the GRUB floppy, but I am certain that GAG doesn't use GRUB on the hard disk.  I am certain that it just boots the WinXP disk.

torgrot

---

### Post by Sbarton on 2007-03-11
You know it's worth while creating your own SuperGrubDisk.Download the .iso and burn it to disk.You will not regret having it by your side. It allows you to experiment knowing you can reinstall grub at any time!
regards.

---

### Post by confused57 on 2007-03-11
> **pe1800 said:**
> I created a GRUB floppy, then booted with the floppy in the drive. I pressed "C". Then used the GRUB command prompt to boot into WXP. It worked!

I wonder though, was that the floppy or the GRUB on the hard drive. How do I know whether the floppy would work when there is no GRUB on the hard drive or when it is damaged?

Thank you!
You "should" see the light on your floppy drive or possibly hear it working...you could always set your bios boot order: floppy, cd, hard drive...place your grub floppy in the drive, put an Ubuntu install cd in the cd drive, then try to boot.  If the install cd boots, then I suppose the floppy isn't working properly.

---

### Post by pe1800 on 2007-03-11
Thank you! Working from the GRUB prompt works with or without floppy. My BIOS is set up in floppy-CD-HD sequence. I will execute the test you suggest.

---

