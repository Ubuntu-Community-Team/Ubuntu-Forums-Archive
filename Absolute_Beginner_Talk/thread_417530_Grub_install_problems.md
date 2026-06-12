---
title: "Grub install problems"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by VEGO on 2007-04-21
Hi there,

I am new with Linux and Ubuntu...I have Fujitsu laptop and XP Home on it. I have made necessary partitions (ext2 and Linux-swap). I successfully  download an image of Ubuntu and burned it on a CD. I boot it from CD and the Ubuntu comes up, no problems.. I do the install and on the very and of an installation process, I get message of grub installation failed, a fatal error. I don't get a message that installation is successful. If I reboot, I get the message no operating system found. My only choice is to boot from my Ubuntu CD. I can't boot windows any more as well. PLEASE HELP!!

---

### Post by nudnik on 2007-04-21
> **VEGO said:**
> Hi there,

I am new with Linux and Ubuntu...I have Fujitsu laptop and XP Home on it. I have made necessary partitions (ext2 and Linux-swap). I successfully  download an image of Ubuntu and burned it on a CD. I boot it from CD and the Ubuntu comes up, no problems.. I do the install and on the very and of an installation process, I get message of grub installation failed, a fatal error. I don't get a message that installation is successful. If I reboot, I get the message no operating system found. My only choice is to boot from my Ubuntu CD. I can't boot windows any more as well. PLEASE HELP!!

Exactly how did you install; what program did you use to partition the disk? How much was allocated to Linux and how much to Windows? What are your PC specs, exactly? What error number is GRUB showing?

---

### Post by VEGO on 2007-04-21
I have notebook with 60Gb HD. Xp are on /dev/hda1 ntfs with size of 45.16GiB
I have made Linux-swap /dev/hda3 with 266.70MiB
For Ubuntu I made /dev/hda2 ext2 8.76GiB
And I have one more partition /dev/hda4 ext3 1.72GiB

---

### Post by VEGO on 2007-04-21
It is a pentium 4 CPU, 1240 SDRAM and it didn't show me any number for grub error, it just said it is fatal error and unable to install grub on (Hd0)

---

### Post by Sef on 2007-04-21
1) Did you md5sum the download?  That checks the download was good or bad.

2) Did you burn the iso at 4x or less?  Faster may cause bad burns.

3) Did you check the disk to make sure it is good?

---

### Post by VEGO on 2007-04-21
No, I didn't but, when I boot from a CD it had an option to check a cd and it was free of errors

---

### Post by YandaPanda on 2007-04-21
Do not feel alone, VEGO! I will try to answer all of your questions at once, Sef.

I have tried to install Feisty Fawn with no success. I went back to an Edgy Eft CD that we have successfully installed on a different system. Both versions of Ubuntu are getting the SAME Grub error (on a system that previously had Win/Mandriva - replacing Mandriva). The LILO put in the MBR by Mandriva is still there, but obviously dies (fatal error) as the reference to the kernel is no longer accurate.

I have tried to change (hd0) - /dev/hda did not work and (hda) did not work. My hard drive is partitioned into hda1 (ntfs/windows), hda2 (swap) and hda3 (Linux ext3)

I installed using the Install icon that is automatically created on the desktop of the Ubuntu Live CD (Feisty Fawn AND Edgy Eft). I was hoping that perhaps backing up to EE and upgrading to FF from there might help. But it is getting the same Cannot Install Grub error. 

Is there a way to install Grub without the hour+ installation of Ubuntu? I have also tried the suggestions of going into the Grub system to find out where it is installed, but that returns the Error 15 (files not found). 

Frustration is mounting and the other versions of Linux are calling me. I would like to join this computer to the Ubuntu family (and have already figured out how to install my wireless adapter, but need to have the system running first!). 

Thanks in advance for any words of wisdom. 

YandaPanda

---

### Post by VEGO on 2007-04-21
I have tried to change (hd0) myself and same result....I like the system and I will not give up. I am sure there is someone to help us

---

### Post by Shmook on 2007-04-21
I had the same problem, tried 3 times to use the livecd to install, but then gave up

Then I burned the alternate cd from the same site I got the livecd .iso (just check "alternate cd for > 256kb RAM machines or something like that at the bottom of the screen) and did the text-based install, which is basically just as guided as the graphical one, and it worked perfect.

---

### Post by VEGO on 2007-04-21
I will try, thanks

---

### Post by VEGO on 2007-04-21
But what is the difference? is that the same system?

---

### Post by YandaPanda on 2007-04-21
Thanks Shmook.I will try that and get back to you all :???:

---

### Post by Shmook on 2007-04-21
mmm????? All I know is that it worked for me where the livecd didn't...also the alternate didn't offer me a choice where grub was setup (hda, hd0...)

---

### Post by YandaPanda on 2007-04-22
Thanks again, Shmook! It appears the installers are considerably different - and in more ways than visual.

Now to figure out my wireless card, which I am not completely sure will work. 

YandaPanda

---

### Post by VEGO on 2007-04-23
I have downloaded and installed the version where the setup is in text mode, now no problems.

Thanks a bunch.

---

