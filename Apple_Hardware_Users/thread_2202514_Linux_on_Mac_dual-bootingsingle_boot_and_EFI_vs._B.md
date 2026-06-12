---
title: "Linux on Mac: dual-booting/single boot and EFI vs. BIOS emulation"
date: 2014-01-29
forum: Apple Hardware Users
---

### Post by zircon_34 on 2014-01-29
[COLOR=#232323][FONT=Verdana]This thread is for people running into booting issues when installing Ubuntu on a Mac.

There is a lot of information out there, but I did not find any satisfying one and would appreciate if somebody can explain that in simple words (since Im a newbie:P). [/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana] 
Its about EFI and where to install the grub boot loader: dual boot vs. single boot linux only. I did not get quite the difference between EFI and Bios emulation, if I dual boot and installed grub on the root partition (\) does that imply I am running a Bios emulation like when you run bootcamp and would install windows? Are people that install only linux on a mac installing grub on the EFI partition? 

(Sorry if thats repetition from a previous thread, but any link or clarification is appreciated as that is important for installing linux on a Mac)[/FONT][/COLOR]

---

### Post by Quackers on 2014-01-29
Your question sounds a simple one, but it is far from simple!
It depends on many things. For example
How was the Ubuntu partition created
On what type of drive (MBR or GPT)
EFI installation or normal (grub)
You can install Ubuntu without any grub installation at all if using EFI (by using the terminal command ubiquity -b to install). In such circumstances Ubuntu will boot by using the EFI stub using something like refind (if you install the correct refind driver in the correct place).
I have no first hand experience of this but I would assume that if you install grub in the Ubuntu's root partition then Ubuntu won't even be a choice in a Mac's boot menu (unless installed in EFI).
Grub cannot be installed in the normal way unless an MBR type drive is used which is not normally the case on a Mac (unless Bootcamped, but that brings up a whole new set of problems).
Grub-EFI now exists though I have not used it, so can't comment on that.

As you can see, not a simple question you're asking.

---

### Post by oldfred on 2014-01-29
Unless you also want Windows do not create the hybrid MBR/gpt drive. That monstrosity was because Windows would only boot in BIOS from from MBR drives and UEFI did not work with Windows.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)


Ubuntu can boot in BIOS or UEFI mode from gpt partitioned drives. 
Mac's converted to UEFI boot with gpt partitioning when they converted to Intel chips. But that was an early UEFI implementation partway between1 & 2, where Ubuntu (& Windows now use 2+ versions).

 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

### Post by zircon_34 on 2014-01-30
You are right Quackers, I guess first I have to read something more about MBR/GPT partitions :popcorn:  I am just thinking of understanding what the basic install (for beginner) of a dual boot vs. single boot described in the Ubuntu how to for Mac is actually doing.  This may also clarify why many people seem to have a problem by booting after installing Ubuntu for the first time on their machine. Most install Grub in the wrong place, or make a mistake during the partitioning phase. 

Thanks Olfred :) for the useful links, I will try to find time to read this! Do you mean its possible to install Ubuntu without making a hybrid partition is that right?

---

### Post by oldfred on 2014-01-30
I have not done it, but that is what those threads say.
And since Ubuntu boots from gpt with either BIOS or UEFI you can configure either way, but do not need MBR at all.

---

### Post by Quackers on 2014-01-30
Yes zircon_34, it's quite a quagmire!
And yes, it's possible to install Ubuntu on a Mac (at least on a mid 2012 retina MBP) as I've done it. I've installed Ubuntu in EFI mode, thus keeping the GPT-only drive.
I did not use grub at all for the first week or so. I installed Ubuntu from the Live desktop by opening a terminal and running ```
ubiquity -b
``` which installs Ubuntu without a boot loader (no grub at all).
However for that to boot you would need to install refind in OSX first. You also need to copy the ext4fs driver from the refind/drivers_x64 (if you're using 64 bit)  directory in the refind package to a self-created "drivers" folder in the main refind installation directory.
This will allow Ubuntu to appear in the Alt + boot menu and to boot from the EFI stub loader.

If required you can install grub later to the Ubuntu root partition using the Boot-Repair utility. This is handy if you want to introduce boot parameters.

Obviously this setup worked for my Apple hardware but until you try it you won't know if it works on yours.

The downside of installing to a MBR type partition is that you effectively limit your system to a maximum of 4 partitions (as MBR cannot handle more than 4). This is a problem in Linux as you may want a swap partition.  Your current Mac (most current Macs) have
an EFI partition as partition 1. Apple only uses this for firmware updates but the partition is required for GPT disks.
an OSX system partition
a recovery HD
as standard. So creating a Linux partition and a swap partition makes a total of 5 partitions. Although this is do-able it means you will need to create a hybrid MBR manually. It is also likely that problems will ensue in the future and for that reason should be avoided.

EFI installation is safer on a Mac, but more involved to accomplish.


EDIT
Also please bear in mind that if your Mac already has a Bootcamp-created Windows installation any further partitioning will break Windows' booting due to the hybrid MBR being incorrect.

---

### Post by zircon_34 on 2014-02-02
Ok, now I got it ;). The basic install tutorial for Ubuntu will lead you to using a hybrid partition table, that is not necessary in MacOS. 

Quackers, since I already had a +- working dual boot Mac/Ubuntu, I wanted to try first (before trying your solution) if I can fix the partition table from a hybrid to an only GPT using [this thread]("http://www.rodsbooks.com/ubuntu-efi/index.html") on fixing the partition table after a basic Ubuntu install. However, I am not sure I managed to configure all the description in the thread correctly as some steps are little tricky for newbies... 

At least I am able to dual boot nicely and in the process managed to fix my login icon issue ([see my thread]("http://ubuntuforums.org/showthread.php?t=2200302")). 

How can I check in ubuntu if my partition is GPT? I used sudo gdisk /dev/sda and got:

```
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 000046A1-0232-0000-8139-00007D720000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 8-sector boundaries
Total free space is 3757 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       195959095   93.2 GiB    AF00  Macintosh HD
   3       195960832       203771903   3.7 GiB     8200  
   4       203771904       217444351   6.5 GiB     8300  
   5       217444352       236976127   9.3 GiB     8300  

Command (? for help): 

```

Is this alright? thanks for comments:-), really appreciate it!

---

### Post by Quackers on 2014-02-02
Excellent!  :D
Have a look at the second line of the gdisk output
MBR: protective
That means that you have a GPT-only disk. It is that way for the whole disk, whatever operating systems are installed.

By what method did you install Ubuntu? By running ubiquity -b in the terminal?

---

### Post by zircon_34 on 2014-02-02
Great good to know!:)

From Quake:
> By what method did you install Ubuntu? By running ubiquity -b in the terminal?

No, I already installed Ubuntu using a live USB ([see my thread]("http://ubuntuforums.org/showthread.php?t=2199210"), post#2), and did not want to loose the data on this computer, so I just followed the fix mentioned in my previous post. I used the terminal commands in MacOS to fix the partition using gdisk and then installed refind and then rebooted. 

I just dont know how to get rid of Grub since for me it would be enough to boot using refind. I am also wondering, would this affect my boot time? now it only takes few seconds...

To Quake: Since your method seems far more simple, I am going to try this for a fresh install on my other mac, thanks for sharing! Will let you know if it worked.

---

### Post by Quackers on 2014-02-02
The only problem with booting from the EFI stub with refind is that you can't enter any boot arguments, should you need to (like nomodeset for instance), or boot into recovery mode.
Or at least I didn't find out how to :)

---

### Post by zircon_34 on 2014-02-02
I just tried 

> ubiquity -b

on the other computer using live XUbuntu, but the generated partition was hybrid, don't know what went wrong. I went to advanced partitioning, there was no Grub loader to install (as expected), I did a Swap, a root and a home partition, ext4. Then rebooted. I could not boot in linux.

I went back to OSX, install gdisk to fix the partition as I did in Post#7 to get a GPT that worked.

However, I could not boot into ubuntu, it did not work for me without grub...

---

### Post by Quackers on 2014-02-02
No, you need refind for that to work and for the ext4fs driver to be copied over. That should boot it.

---

### Post by zircon_34 on 2014-02-02
yes I had refind installed and the driver (ext4_x64) copied (to /EFI/refind), but when I chose the Ubuntu icon at startup, it brought me to a command line black screen (gnu grub v. 2 something like that, but its not the normal grub load screen). not sure what went wrong.on the other mac I did not have this problem...

It maybe because I tried XUbuntu and not Ubuntu install, but the point is that when I went in the terminal in MacOS and checked my partition using disk, I had a hybrid partition table. But I though using the ubiquity install should create a GPT partition table...

---

### Post by Quackers on 2014-02-02
Yes indeed you would think so.
I installed in that way and did not have this problem.
However, interestingly enough I have recently installed Ubuntu 13-10 using (mostly) this guide
[https://help.ubuntu.com/community/MacBookPro11-1/Saucy]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy")
and all was fine - OSX< Windows 8.1 and Ubuntu all booted fine.
I then ran all pending updates in Ubuntu and rebooted to OSX when finished. It wouldn't boot. I traced the problem to a hybrid MBR being present. It certainly wasn't there when I installed everything. I have no idea how it got there but I reverted to a protective MBR with gdisk and everything has been fine since.

So, who knows? Not me!

---

### Post by zircon_34 on 2014-02-02
hahaha:D

At least thanks for the good advices, I learned how to fix a partition table and creat a dual boot using GPT!

---

### Post by Quackers on 2014-02-02
Yes, don't lose gdisk. I couldn't live without it now. It's invaluable.
Kudos to its creator srs5694 who used to be a member here.

---

