---
title: "New Ubuntu Install"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by mtime2457 on 2007-08-13
Hello,

I'm new to the linux world and I'm going to attempt to install Ubuntu on a 30gb Maxtor hard drive.  I was wondering what would be the best way to partition my hard drive.  Should I go with the default settings?  Or should I have a certain number of partitions?

I'm also going to dual boot the workstation with Windows XP on one hard drive and Ubuntu on a totally separate hard drive.  Is there anything special I have to do to get grub to work correctly?  I want to be able to choose which operating system to boot from.

One last note...I will be installing Ubuntun 6.0.6

---

### Post by ron999 on 2007-08-13
Hi
If you're new to Ubuntu then I think that you ought to use default settings, don't try anything fancy.
When you install Ubuntu on your 30GB drive it will put GRUB on the beginning of that drive.
You will need to set your BIOS to boot from that drive.
Afterwards you will probably need to add the Windows information to the GRUB menu yourself.
Ask about this later, I think.

---

### Post by myk.dinis on 2007-08-13
My setup is similar...

except I have 3 physical disks and 5 logical...

I put winXp on the smaller of the three... did an answer file install and changed the docs and settings folder to a separate drive (the second biggest formatted fat32) and I have ubuntu on the larger with 3 partitions...15GB for / , 1gb for swap and 63gb for /home...

The docs and settings drive and the 63gb /home drive may seem redundant...but I have all the shared docs (all the stuff everyone uses) sitting on the fat32 drive...and all my files live on the 63gb one...

more info later...

---

### Post by Hospadar on 2007-08-13
Hello! 
> Should I go with the default settings?  Or should I have a certain number of partitions?
if you are able to use the whole drive (you don't have let's say, a windows or data partition that you want to save) I would just go with guided partitioning using the whole disc.  this will format the entire disk with a small swap partition and an ext3 data partition.
> Is there anything special I have to do to get grub to work correctly?
Well you will want to make sure that you don't overwrite the mbr (master boot record) on the windows hard drive, because then you'll have to go through a somewhat tricky and rather annoying process of restoring the windows boot loader so you can load windows.
What you will want to do is make sure that grub gets installed on the same disc you are installing the hard drive.  There are two ways to assure this happens
-temporarily unplug the windows drive
-near the end of the installation dialog, there will be an "advanced" option (after you select your partitions) that will give you a choice of which drive to install grub on, make sure that the drive selected here is the drive you are installing ubuntu onto.

Once you have gotten ubuntu installed, you'll want to make sure of two things: the drive that ubuntu & grub are installed on is selected as the primary boot device; and second, if your hard drives are IDE drives (the big wide ribbon as opposed to the little red/yellow cable) that the drive you installed ubuntu on is plugged into the "master" plug on your ribbon cable (this is the plug in the middle of the cable)

Ideally, this will then allow you to boot into grub, and select your os.

Also, I would *highly* recommend installing 7.04 instead of 6.06, fiesty is really much better (LTS just means it stays in the repositories longer, it isn't really better for the average user at all).  If you have an older machine and are looking to save on resources, you may want to look into xubuntu.

---

### Post by qamelian on 2007-08-13
> **ron999 said:**
> Hi
If you're new to Ubuntu then I think that you ought to use default settings, don't try anything fancy.
When you install Ubuntu on your 30GB drive it will put GRUB on the beginning of that drive.
You will need to set your BIOS to boot from that drive.
Afterwards you will probably need to add the Windows information to the GRUB menu yourself.
Ask about this later, I think.

Not so. If both drives are installed in the PC and Ubuntu is going on the second drive, the default is for GRUB to install to the MBR of the first (Windows) drive. If the install goes correctly, which it usually does, GRUB will be automatically configured to allow booting of either OS. There is no need to change any settings in the BIOS.

---

### Post by ron999 on 2007-08-13
> **qamelian said:**
> Not so. If both drives are installed in the PC and Ubuntu is going on the second drive, the default is for GRUB to install to the MBR of the first (Windows) drive. If the install goes correctly, which it usually does, GRUB will be automatically configured to allow booting of either OS. There is no need to change any settings in the BIOS.

OK

I installed Ubuntu with my Windows drive disconnected then I had to add extra lines to the GRUB menu myself.

---

### Post by qamelian on 2007-08-13
> **ron999 said:**
> OK

I installed Ubuntu with my Windows drive disconnected then I had to add extra lines to the GRUB menu myself.

I kinda fiugred. It seems like a lot of people go that route, mostly because they're paranoid about letting anything mess with the MBR on their Windows drive. I just don't worry about it because, in 10 years of using Linux, I've never had a dual boot problem.

---

### Post by mtime2457 on 2007-08-13
> **qamelian said:**
> I kinda fiugred. It seems like a lot of people go that route, mostly because they're paranoid about letting anything mess with the MBR on their Windows drive. I just don't worry about it because, in 10 years of using Linux, I've never had a dual boot problem.

So if I install Ubuntu on a secondary hard drive which will be the slave hard drive, I shouldn't have a problem?  Meaning, I should get grub to come up and ask which operating system I want to boot from?

Appreciate all the feedback!:guitar:

---

### Post by myk.dinis on 2007-08-13
ok...so the more info...

if you are doing 2 disks I would suggest installing windows first...

then installing linux...and let GRUB take care of the boot load process...that way you see both OS's...if you want to have win handle the boot process...i.e. boot.ini I would suggest having the instructions printed and in front of you b4 the install of either...there are several write ups how to do it this way...

basically, you need a / partion and a swap partition and a /home...

the only reason I even say /home is so if you need to re-installl your os you can always keep all tyour good stuff...

remember xp should be ntfs, linux (whatever you think is best, I like ext3, others prefer others...it's like distros of linux) and if you want any shared partitions between xp and linux you should have that ne fat32...they can both read and write to it without special permission crap...

best of luck!

---

### Post by mtime2457 on 2007-08-13
> **myk.dinis said:**
> ok...so the more info...

if you are doing 2 disks I would suggest installing windows first...

then installing linux...and let GRUB take care of the boot load process...that way you see both OS's...if you want to have win handle the boot process...i.e. boot.ini I would suggest having the instructions printed and in front of you b4 the install of either...there are several write ups how to do it this way...

basically, you need a / partion and a swap partition and a /home...

the only reason I even say /home is so if you need to re-installl your os you can always keep all tyour good stuff...

remember xp should be ntfs, linux (whatever you think is best, I like ext3, others prefer others...it's like distros of linux) and if you want any shared partitions between xp and linux you should have that ne fat32...they can both read and write to it without special permission crap...

best of luck!



Windows XP Pro is already installed on the master drive, all I'm doing is adding a second hard drive and installing ubuntu on it.  I just want to make sure that Grub will be installed on the master hard drive so I can pick and choose which operating system to boot.

---

### Post by ron999 on 2007-08-13
> **mtime2457 said:**
> Windows XP Pro is already installed on the master drive, all I'm doing is adding a second hard drive and installing ubuntu on it.  I just want to make sure that Grub will be installed on the master hard drive so I can pick and choose which operating system to boot.
Yes, see qameliain's post #5. My previous advice was duff.

---

### Post by qamelian on 2007-08-13
> **ron999 said:**
> Yes, see qameliain's post #5. My previous advice was duff.

It works though. Just a different approach to the same or similar end result.

---

### Post by mtime2457 on 2007-08-13
Ok, so I installed Ubuntu on my secondary hard drive and now when I reboot I receive Grub error 18.  Apparently there is a problem with the Master Boot Record.

---

### Post by mtime2457 on 2007-08-14
FYI:  this is how I fixed the Grub loading....please wait error 18

[http://ubuntuforums.org/showthread.php?t=524953](http://ubuntuforums.org/showthread.php?t=524953)

---

### Post by ron999 on 2007-08-14
Hi
I'm glad you got it fixed.
Please tell me, in the end, do you have XP on your main drive and Ubuntu on your second drive.
And is GRUB on the Windows drive?

---

### Post by bayvista on 2007-08-15
Yes, well that's what I have and Windows does not appear in my GRUB. How do I add it?

David

---

### Post by mtime2457 on 2007-08-29
Hello Ron,

I apologize for the delay, but in the end Ubuntu and Grub are installed on the master drive and Windows SP Pro on the slave drive.  Also,  when I installed Ubuntu I had both drives (master & slave) connected.  When Ubuntu asked me what drive to install Ubuntu on I selected the master drive and made the / root partition bootable.  The main partition on the slave drive with Windows XP Pro is also marked as bootable (I didn't have to make this change since the Ubuntu install already noticed Window XP Pro on the second drive).  At the end of the installation I installed Grub on the master drive with Ubuntu and right before the installation finished a Grub window showed up asking me if I wanted to add Windows XP Pro to the Grub menu.  I selected yes and all this did was to add Windows XP Pro on the slave drive to the Grub Menu.

---

### Post by ron999 on 2007-08-29
Thanks mtime2457
That seems like a good setup.

---

