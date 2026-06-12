---
title: "GUID vs MBR, single boot on a macbook"
date: 2007-03-17
forum: Apple Intel Users
---

### Post by macLuntu on 2007-03-17
Hi.

I am trying to set up Ubuntu 6.10 as the only operating system on my macbook. I have currently tried three different  methods. They all work but I don't like any of them. Here is the description and the major pros and cons.

Method 1, using GUID partition table with rEfIt: Install OS X, create two partitions both hfs+. The first partition is only 20 MB, and the second doesn't matter cause I'll delete it later. Install osx to the second partition. Then download and install rEfIt on the 20 MB partition. Boot LiveCD, delete osx partition, and install Linux.
Pros: Boots much faster because you can set in refi.conf to timeout in e.g 2 seconds
Cons: EFI creates one partition automatically as soon as you use the GUID partition table. When I manually create a second partition to get the graphical menu and tools. I have allready used 2 primary partitions on the disk.  Very time consuming.

Method 2, using GUID: Boot os X and sett GUID partiton table on disk (if not allready). Install from live cd. 
Pro: Farly easy
Cons: Takes 20 second before  linux starts  to boot and then there is the EFI partition again.

Method 3, using MBR: Boot live cd --> Erase enitre disk. (or setup MBR with Osx disk utility)
Pro: easy
Con: Takes 20 seconds before linux starts  to boot

Qustion: I prefer method three because then I don't have to worry about syncing GBT/EFI.  It's easier to setup, and creates less partitions. Is there a way to speed up the  booting process???

I am getting desperate here.. any ideas?  :confused:

---

### Post by das_syndrom on 2007-03-17
Question: Why do you have to wait for 20 seconds before ubuntu starts in methods 2+3? Is there a particular reason?

I have not tried to set up a single boot system yet. (I don't have the time atm and I'm waitung for feisty) Currently I have a dual boot (OSX+Linux) Setup, but I never use MacOS.

Andi

---

### Post by rei_t_ex on 2007-03-17
I am single booting to Ubuntu on one of my Macbooks (white CoreDuo 2Ghz).  Being completely new to Linux when I installed it (and being used to everything just working out of the box), I never read any HOWTOs, simply popped the LiveCD in, selected install, and chose to erase the entire disk.

And everything just worked!  It boots immediately as well, without any 20 second wait...

---

### Post by macLuntu on 2007-03-17
das_syndrom: I don't know..  In method 2 i thought it had something to do with EFI stuff timing out in 20 secs. That's the default  timeout when installing rEFit. As I said don't know.. just assumed.

Why the MBR doesn't boot straight away like it does on rei_t_ex's macbook.  That's what I was hoping someone could tell me.

BTW:The Macbook is a white C2Duo 2.0 GHz  with 2 GB RAM.

---

### Post by hoover on 2007-03-24
I have the same problem. If try to do a single boot (White core2duo) The screen goes blank for about 30 seconds and THEN boots up linux.

hoovs

---

### Post by macLuntu on 2007-03-27
I wonder if this is only a problem on the C2D's?!?

---

### Post by Zelut on 2007-05-06
I tried simply installing Ubuntu solo on my C2D machine and it wouldn't boot afterwards.  The closest I've been able to get is OSX + bootcamp + rEFIt + Ubuntu.  I've set Ubuntu as the default and it boots after just 3 seconds (updated the boot config).  I would prefer to simply have Ubuntu on this machine, solo.  Any tutorials on doing this?

---

### Post by benanzo on 2007-05-06
The reason that Ubuntu takes so long to boot if installed as the only OS is because the EFI scans the GUID Partition Table thoroughly before checking the MBR.  Since GRUB installs to the MBR, we just have to wait for the EFI to find it, then Ubuntu will boot.

I have the same problem.  I have Feisty installed as the sole OS on my first-gen MacBook Core Duo (not Pro or C2D) and I look at that grey screen forever and even sometimes get the folder with the ? in it (indicating it can't find a bootable disk) until finally the EFI finds GRUB on the MBR and then I boot fine.


I have been scouring relentlessly for info on getting ELILO or GRUB2 to boot 32-bit Feisty kernel in pure EFI/GPT environment without using the MBR or any emulated BIOS business.  That should enable us to set our boot parameters directly in EFI rather than going through rEFIt for a multi-boot setup.

So far I am hitting a wall though.  It seems that ia64 kernels contain the necessary EFI code to properly interact with the EFI.  When I apt-get install elilo it pulls down a little utility called efibootmgr which is supposed to allow access to the EFI boot parameters.  The only problem is that it requires kernel module efivars to be loaded, which doesn't exist in the stock 32-bit Feisty kernel (I'm running 2.6.20-15-generic).  So when I try to set up elilo I get some errors about failing to update the EFI boot settings.

According to some of the debian lists, ia32 kernels have supported EFI natively for ~2 years.  (These were old lists I was looking at.)  I'm not sure if the disconnection happened when Ubuntu sync'd with the debian kernels or if EFI support was removed from the ia32 stuff.


UPDATE:

[https://launchpad.net/ubuntu/gutsy/+source/elilo-installer/1.11ubuntu1](https://launchpad.net/ubuntu/gutsy/+source/elilo-installer/1.11ubuntu1)

this is a changelog for elilo-installer.  It states clearly that it is design for i386 and ia64.  it also mentions support for Apple Intel Macs.  It is also being targeted for Gutsy.  *Hopefully* we will get this going sometime this summer (I don't want to wait for Gutsy.)

I'm still confused about what happened to the code from debian.
Good news though.

---

### Post by sooqing on 2007-05-15
getting a macbook soon to run feisty solo.. thus wiping off entire disk.. does this problem still exists?

---

### Post by ronocdh on 2007-05-15
> **sooqing said:**
> getting a macbook soon to run feisty solo.. thus wiping off entire disk.. does this problem still exists?
Judging by benanzo's "update," the issue still does apply. Tangentially, I'd like to recommend, as I have countless times in the past, that one pare down the OS X installation (by removing unwanted modules during installation, such as foreign languages and iLife applications) and keep it on a small partition. It can be very useful for firmware updates into the future, which will not released to Linux. Also, for the time being, your boot-up time can be substantially reduced just by keeping OS X on an unused partition. Edit your rEFIt settings to make Ubuntu the default OS and reduce the countdown time to 3 seconds or so.

---

### Post by Zelut on 2007-05-15
I agree.  I considered wiping it as well but the latest Apple update gave me nearly a half-hour extended battery life and boosted my wireless signal.  I'm content, just for that, to keep a smaller 5-10G OS X partition there.

Leaving OS X and refit on will also speed up boot time too... just something to think about.

---

### Post by macLuntu on 2007-10-22
Has anyone tested if this problem is solved with the latest efi-firmware update from Apple?

---

### Post by dustynus on 2008-06-26
Problem I have is that I have lost my osx install cd's.
All I have is ubuntu on the macbook, and It loads into the grey mac screen where I have to wait about 30 seconds+ before it loads grub.

Any suggestions on what to do with only ubuntu on the macbook to try and fix the situation ? 
Is it possible to install refit without osx ??

---

