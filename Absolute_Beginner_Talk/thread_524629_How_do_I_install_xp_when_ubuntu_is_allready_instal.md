---
title: "How do I install xp when ubuntu is allready installed?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Dalston on 2007-08-13
Hello

The title says it all really...  I have 2 hard drives,  the first is a 250g with Ubuntu 7.04 installed and the other is a 150g set up as a ext3 for storage.  What I want to do is install xp on the first hard drive so I can dual boot,  is it possible to repartition the first hard drive so that I can install xp or as I have already allocated the whole drive for Ubuntu is this not possible?

Thanks in advance

---

### Post by bodhi.zazen on 2007-08-13
Yes, you can preize your ubuntu partition with gparted. It is on the Ubuntu CD.

GParted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)


After installing Windows you will need to restore grub :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Hobo Joe on 2007-08-13
Just shrink your Ubuntu partition, and leave however much space you want at the end. Make sure to leave it unallocated.

Then when you install Windows, just select the 'unpartitioned space' and format it to NTFS.

You'll have to repair GRUB though, see the link that bodhi.zazen gave.

---

### Post by Dalston on 2007-08-13
I have gparted already installed but because im trying to reformat the partion the os is on it wont let me.  Or do you mean I have to use the live cd to access the boot up screen?

---

### Post by diatribe on 2007-08-13
yes you have to use the gparted/ubuntu livecd, you can not edit mounted partitions

---

### Post by Dalston on 2007-08-13
Ok I tried to use gparted on the live cd,  could someone tell me approx how long its meant to take?   I tried to resize a 250g down to 200g I left it for 160 mins and it had still not completed.

---

### Post by Dalston on 2007-08-13
> **bodhi.zazen said:**
> Yes, you can preize your ubuntu partition with gparted. It is on the Ubuntu CD.

GParted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)


After installing Windows you will need to restore grub :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

thanks for the info

---

### Post by Dalston on 2007-08-14
How long does gparted take to resize a drive?  because I left it running for 2 and a half hours and it still hadnt finished.

---

### Post by nvrpunk on 2007-08-14
That depends on Processor, Hard Drive Speed and Size.  Should take a while :)

up to 8 hours on a laptop? my guess.  prolly 4 for what you are doing.

---

### Post by Dalston on 2007-08-14
> **nvrpunk said:**
> That depends on Processor, Hard Drive Speed and Size.  Should take a while :)

up to 8 hours on a laptop? my guess.  prolly 4 for what you are doing.

Oh ok, I thought it had gone wrong when it went past 2 hours.  Its a 250g hard drive,  I guess i'll have to do it overnight.

Thanks for the help.

---

### Post by Dalston on 2007-08-24
Ok I finally shrunk the 250g drive down to 200g,   now im gonna install XP but can you help me with how to install the grub after, i've read the link you posted but im a bit unsure.

---

### Post by Dalston on 2007-08-27
Could someone talk me through the process of installing the grub after xp is installed,  I have downloaded the Unofficial "Super Grub Disk" and burnt it to disk but b4 I install xp I want to be 100% sure I know what im doing.

---

### Post by bodhi.zazen on 2007-08-27
See either the lilnk I gave you re: re-installing grub after windows or try this one :

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no)

---

