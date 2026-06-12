---
title: "[SOLVED] Create bootable CD from DOS diskette image"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-09-16
Here's another "dumb" question from me.  First the "why", then hopefully someone can help me!:)

I need to install Windows again in order to try out the "ops" program version 21 for accessing CVS camcorders.  I tried just using a virtual machine with Win 98SE in it, but it didn't find the camera on the USB. So, I want to re-install Windows 98SE to a small partition and dual-boot.

I have my Win98SE cd, the problem is that the floppy drive is not working in this junk desktop.  I have an image file (extension of IMA - worked for booting the VM) of the boot floppy, but I need to burn it to a CD somehow so that it is a bootable image.  

So, I don't have a clue on how to do this!  Can anyone help me?:):)

Thanks in advance!

---

### Post by mocoloco on 2007-09-16
Have you tried just putting the Win98SE boot disk files on a CD?  I would think it would work.  You can get the files [here]("http://www.bootdisk.com/bootdisk.htm"), and run the exe if you have wine.  I've used the 98SE OEM file from that site and it works great, the only problem is it requires you to insert a floppy to write to ;).  You can probably find the files somewhere though.  Or, crazy thought, if your VM lets you mount a floppy file you could run that bootdisk maker in the VM to get the files and put them on a CD to see if it will actually let you boot from it.
Phew. This is a fun one. I'd like to hear how it turns out.

---

### Post by mocoloco on 2007-09-16
I just remembered something.  When you boot from the floppy it loads DOS without CD-ROM support, then loads the mscdex driver to allow use of the CD-ROM.  So that makes me think it probably won't work :(.  Maybe someone's created a modded bootable 98 disc.

---

### Post by anewguy on 2007-09-16
Here's the  REALLY sad part - I had created a bootable CD including Win98SE so all I needed was a single CD.  You could run setup right off it after it booted, or you could run fdisk, format and then setup.  But, wouldn't you know, that has disappeared!  Since I don't seem able to get the floppy drive to work (even in the VM the floppy drive appears to be broken), I may need to end up tracking down the boot.ini, etc., files, and then copies of the fdisk, format and mscdex to get things working.  Sure wish I hadn't lost that CD I made!:):)

Thanks for the replies, and if someone else has some ideas please post them!  I'll let you know what I did to get things working when the time comes.

Too bad there isn't a version 21 of ops that will run in Linux.  I've tried ops-for-linux, but all it does is find the camera but can't unlock it.  Another post in the camerahacking site said that for the same version of firmware you have to use version 21.

Thanks again!:)

---

### Post by anewguy on 2007-09-16
I've been trying to get mkisosf to work to generate an iso image I can burn to the CD.  It appears to use genisoimage in Ubuntu, so I've been using that.  I have it down now to where it thinks the diskette image isn't a valid image.  Anyone know why this would be?:)

---

### Post by anewguy on 2007-09-16
I finally just found an ISO image for a Win98SE boot cd, so I downloaded it, burned it and it worked fine.:)

---

