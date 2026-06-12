---
title: "[SOLVED] Install Xubuntu on empty PC"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by erable on 2007-10-04
I wish to install Xubuntu on an old Dell Latitude with 64MB.
The Xubuntu 7.04 Alternate i386.iso CD seems not bootable (Message: non valid system disk; I/O error). I've configured the BIOS to boot from CD.
I have to say that the whole disk of the PC was formatted so there's absolutely nothing on the hard drive. The PC & disk were operational before the formatting took place.
There is no floppy drive available.
Thanks a lot for your help.

---

### Post by voided3 on 2007-10-04
Hmm, well either the disk was burned incorrectly or the computer is trying to boot from the hard disk. On many older computers they need a floppy drive with a boot diskette to boot from a cdrom, so perhaps the latitude has a either a hot swappable floppy or an external floppy attached via serial cable or the like. If possible, test to see that your alternate disk is bootable on another machine. If so, you may need to setup some kind of boot loader on the latitude. I've heard of people installing via a network boot from another system as well, so that may another option. Good luck!

---

### Post by erable on 2007-10-04
The PC on which I've burned (up to 3 copies from 2 different downloads) the alternate CD does not want to boot from it either.
Is Xubuntu 7.04 Alternate i386.iso really a bootable entity ???
Thanks,

---

### Post by voided3 on 2007-10-04
Out of curiosity, and you probably already know all of the following, but try this: put the CD in a computer that is already booted up (any OS) and look at it in a file manager. Is there only an ISO image or is there a bunch of directories/folders like "bin" and "etc"? If there is only an ISO image file, then the CD is merely burning a data disk and not a bootable image. Burning ISOs varies depending on your burning software, so if that is the case, consult the program's help file or website.

---

### Post by overdrank on 2007-10-04
> **erable said:**
> The PC on which I've burned (up to 3 copies from 2 different downloads) the alternate CD does not want to boot from it either.
Is Xubuntu 7.04 Alternate i386.iso really a bootable entity ???
Thanks,

HI maybe these links will help
 this "how to" to burn the cd
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And you can verify the cd also because it could have been corrupted during the download
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by erable on 2007-10-05
Thank you both for your valuable help. Never burned a bootable CD b4 so it's all new.
Since the .iso file shows up as a Roxio file I used Roxio to burn a bootable CD (with no floppy emulation). The result was a CD with 2 files on it: bootcat.bin (2MB) and bootimag.bin (the size of the original .iso file).
But the CD isn't bootable on the PC I used to burn it. For fun I doubleclicked on the bootimag.bin file when I was under Ubuntu and a KATE window opened, but nothing happened.
I'll follow the other hints further (alternative CD burning SW & quality check of the download).
I am impressed by the speed and quality of your replies.
Hopefully I can change the status of the thread to 'solved' next time I visit the forum.
Till then.

---

### Post by erable on 2007-10-05
Progress being made but ...
Could boot Xubuntu on my laptop from CD burned with Infrarecorder. Ran CD-ROM check with Xubuntu and CD was declared OK although the sumcheck calculated by winMd5Sum was way off the publicised hash table's value !
But the target machine (Dell Latiude cpt) still won't boot, which was the purpose of the exercise.
Does it require another (older) older format of the boot disk ???? Any idea ?
Thank you in advance

---

### Post by overdrank on 2007-10-05
> **erable said:**
> Progress being made but ...
Could boot Xubuntu on my laptop from CD burned with Infrarecorder. Ran CD-ROM check with Xubuntu and CD was declared OK although the sumcheck calculated by winMd5Sum was way off the publicised hash table's value !
But the target machine (Dell Latiude cpt) still won't boot, which was the purpose of the exercise.
Does it require another (older) older format of the boot disk ???? Any idea ?
Thank you in advance

Ok do you know if the cd drive is good? Yes if the checksum is off then the cd is not good. And lastly the system only has 64mb ram ( only the alternate cd of xubuntu will work) if it has a onboard graphics then it shares that memory and that will cause problems.

---

### Post by Hallvor on 2007-10-05
> **erable said:**
> I wish to install Xubuntu on an old Dell Latitude with 64MB.
The Xubuntu 7.04 Alternate i386.iso CD seems not bootable (Message: non valid system disk; I/O error). I've configured the BIOS to boot from CD.
I have to say that the whole disk of the PC was formatted so there's absolutely nothing on the hard drive. The PC & disk were operational before the formatting took place.
There is no floppy drive available.
Thanks a lot for your help.

64 MB of memory is way too little. You need at least 128 - preferably 256 or more. Try Puppy Linux or Damn Small Linux instead. Xubuntu 7.04 isn`t really that lightweight.

---

### Post by erable on 2007-10-06
Since I was able to create a bootable CD the only thing left is to find out is what's wrong with the Dell laptop. Guess this ain't the place to discuss that particular issue.
Thanks for all your help !

---

