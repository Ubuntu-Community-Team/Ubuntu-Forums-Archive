---
title: "Boot error"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Garavan on 2008-03-09
Installed 7.10 from the CD, downloaded available updates and tried to restart the system, It  generated an error message that it is unable to boot.  Now I'm using the live version and the result of sudo fdisk -lu is:
Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36e0a602

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   586067264   293033601   42  SFS

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0dde0ddd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1441753424   720876681   83  Linux
/dev/sda2      1441753425  1465144064    11695320    5  Extended
/dev/sda5      1441753488  1465144064    11695288+  82  Linux swap / Solaris

Whereas, hda contains my data from the Windows XP machine and sda should have the ubuntu on it. Both can be accessed while using the live CD.

Can this cause the problem? What can I do to be able to start ubuntu?

---

### Post by EvilBro on 2008-03-09
It usually helps to give the exact error message that it produces. If I would have to guess, it is probably some kind of GRUB error message. Search for GRUB error on this forum.

---

### Post by Garavan on 2008-03-09
In order to give you the exact error text I've to quit, but thenI need to reinstall everything. Exactly that part what I wanted to avoid. By the way, what is GRUB stands for and how could I access it? Keep in mind, that I just tried to install the OS to became familiar with it.

---

### Post by EvilBro on 2008-03-09
> **Garavan said:**
> In order to give you the exact error text I've to quit, but thenI need to reinstall everything.
Why? You can just boot (or rather fail to boot) once, write down the error and then start with the LiveCD again, can't you?

---

### Post by sandysandy on 2008-03-09
> **Garavan said:**
> In order to give you the exact error text I've to quit, but thenI need to reinstall everything. Exactly that part what I wanted to avoid. By the way, what is GRUB stands for and how could I access it? Keep in mind, that I just tried to install the OS to became familiar with it.
 have a look at this site 

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

to quote 

[I]GRUB stands for GRand Unified Bootloader.

GRUB is a Multiboot boot loader.

Briefly, boot loader is the first software program that runs when a computer starts. It is responsible for loading and transferring control to the operating system kernel software (such as the Hurd or the Linux). The kernel, in turn, initializes the rest of the operating system (e.g. GNU).[/I]

regards

---

### Post by Garavan on 2008-03-09
This is the exact error message:
Error loading operating system

This message is displayed within the restart process while still in BIOS.
The only thing it will allow is to reinstall ubuntu from scratch, which I do it right now.
I even disconnected the hda, so I'm only using sda to reduce problem sources.
While it is installed, it seems to work great until I try to restart.

This is the problem !!!!!!!

Thanks on the GRUB explanation.
.

---

### Post by EvilBro on 2008-03-09
As that message is a BIOS message, I'd expect the problem to lie in the BIOS somewhere. The disk is properly detected by the BIOS? (edit: I've googled a bit and all links seem to suggest that you have to set the disc to LBA in the BIOS. I searched with the error message as search-text. See for yourself to see whether the same situation applies to you.)

---

### Post by Garavan on 2008-03-09
Great, it is now working fine.
It is obvious that ubuntu get messed up with 2 disk drives, because after removing hda the sda suddenly worked.

It should be stated somewhere at the beginning of the installation to NOT to install ubuntu with multiple or mixed disk environment (whatever the case is). It would greatly reduce frustrations especially by newbies.

Thanks for all the comments anyway.

---

### Post by EvilBro on 2008-03-09
> **Garavan said:**
> It should be stated somewhere at the beginning of the installation to NOT to install ubuntu with multiple or mixed disk environment (whatever the case is).
You are assuming that because you had problems with this, everybody has problems with this. That is not the case. I've installed ubuntu on a multiple/mixed disk environment and I didn't encounter any problems. A warning would only be warranted if the probability of failure was large enough. I don't see any indication that it is.

Also, I think it is your BIOS that is getting confused.

---

### Post by ajgreeny on 2008-03-09
Multiple disk systems don't usually cause the problem you've had, so there is no need for a frightening message before booting and installing.  Did you have both disks installed in the machine when you installed or did you disconnect the windows one to avoid possible problems?  If you disconnected, that will be the problem as the system will have named the disks wrongly for grub when you reconnect the windows disk.  If you did not, then you have been unlucky that grub did not sort out disk nomenclature correctly.

---

### Post by Garavan on 2008-03-09
Obviously it was my fault not to describe precisely what happened:
I built a new PC x64 AMD Dual Core with a SATA disk drive (referred as sda). It was working right away under Windows XP. So I decided to move my hard drive (referred as hda) containing only data files (docs, music and movies) from an old PC to the newly built one and installed ubuntu. The installation resulted to the BIOS - Error loading operating system.

Once I disconnected the hda cable from the Mobo, the OS started and is running.

And at that time I posted the message that there is a problem when either more then one disks are connected or their  are mixed (sda hda).

Therefore please tell me what should I do to reconnect my hda to access my data and be able to boot the system. I really would keep my data on a separate disk installed on the new PC.

Thanks for your advise.

---

### Post by Duck2006 on 2008-03-09
The problem was most likely in your BOIS, as to what drive was set to boot first, ie IDE, SATA, ect.

---

### Post by Garavan on 2008-03-09
More good news

After GG was up and running, I reconnected my hda and voila, all the files could be accessed and no I've no more problem booting the OS.

---

### Post by retrosteve on 2008-03-11
I just installed Ubuntu for the first time, overwriting a Win XP drive, and had the exact same problem.

Error loading operating system.

It's not the boot device order, I can switch that around and it makes no difference.  this machine is unable to boot from the DVD drive (which is USB) anyway.

Before I installed, I was having major difficulty because I couldn't get the Ubuntu CD to boot.  USB CD drive.

Now I can't do anything with the computer at all.

I guess any help would be appreciated.   My first experiment will be as the above poster tried, to disconnect the other hard drive.

---

