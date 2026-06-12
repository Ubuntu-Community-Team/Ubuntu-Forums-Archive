---
title: "Serious Problem With GRUB-- Urgent"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by travismh on 2007-11-26
I installed Ubuntu but it failed mid way through, so I had to restart it again, though it keeps freezing.  I decided to use windows XP, but all I get is ´GRUB_´   

What does this mean?  Windows XP or even Ubuntu is not working properly, I just recieve that GRUB message and nothing else, and when I try to type in a command it doesn´t show anything, it just says GRUB_

I need help urgently, because no OS seems to be working on my system.

I have an IBM thinpad T23, and I tried to delete GRUB from the BIOS menu but I can´t find it as an option.

Help me please, thank you. 

How do I get rid of GRUB?

---

### Post by spiderbatdad on 2007-11-26
You can't just delete Grub. It has been installed as your boot loader in place of the Master Boot Record. It sounds like you may have installed a corrupted disk. Did you do a MD5SUM check before installing the disk. I believe your only hope now is to burn a good iso on another system, burn at slowest possible speed, and verify the MD5SUMs.

If you want to return to Windows XP, you will need a recovery disk, as your software was probably pre-installed. It used to be possible to recover from IBM.com,, now Lenovo, but I think they have changed their policy and require around $100.00 to send you a recovery disk. Not entirely sure about that last part. Check out their support site.

---

### Post by Taboo Mirage on 2007-11-26
He may not need a XP recovery/installation disk; you're assuming Windows is hosed.  It could merely be a GRUB configuration/installation error as the installation "froze half way through."

Suggest checking out the Super Grub Disk:

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

Use that to reinstall the Windows bootloader.  You should be able to reboot into Windows with that.  Alternatively if you have it you could use an actual Windows disk and go to a recovery console and type:

```
fixboot
fixmbr
```

---

### Post by master_kernel on 2007-11-26
> **Taboo Mirage said:**
> He may not need a XP recovery/installation disk; you're assuming Windows is hosed.  It could merely be a GRUB configuration/installation error as the installation "froze half way through."

Suggest checking out the Super Grub Disk:

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

Use that to reinstall the Windows bootloader.  You should be able to reboot into Windows with that.  Alternatively if you have it you could use an actual Windows disk and go to a recovery console and type:

```
fixboot
fixmbr
```

I agree with the Super Grub Disk suggestion. It's saved me and my computer many times!

---

### Post by bw44 on 2007-11-26
> **travismh said:**
> I installed Ubuntu but it failed mid way through, so I had to restart it again, though it keeps freezing.  I decided to use windows XP, but all I get is ´GRUB_´   

What does this mean?  Windows XP or even Ubuntu is not working properly, I just recieve that GRUB message and nothing else, and when I try to type in a command it doesn´t show anything, it just says GRUB_

I need help urgently, because no OS seems to be working on my system.

I have an IBM thinpad T23, and I tried to delete GRUB from the BIOS menu but I can´t find it as an option.

Help me please, thank you. 

How do I get rid of GRUB?

Don't panic yet!  I am not an expert and have not had to recover from the situation you are in, but you may be able to restore the MBR record to point to your  Windows partition. In other words, your XP system is probably still OK, but the Master Boot Record now points to GRUB.  You need to run a utility to restore the MBR to the state it was in when Windows owned your system.  Here is a URL that describes  this specific operation:

[http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector](http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector)

The above page is part of an amazing site in which the author has described a lot of things you need to know about your dual boot environment.  Before you attempt anything rash read all that the site has to say about dual booting and, GRUB and so on.  If the above procedure doesn't work, you may be able to create a Super Grub Disk and use it to recover:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Or a Linux recovery CD that will help.  The URL for this site is:[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page).

There  is also at least one thread about GRUB errors to which the author of the above mentioned site contributes.  You might try posting to that thread and get some personal attention from a real expert: [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

As the author of the Super Grub page above says:

"If you are experiencing booting problems, the most important thing to do is to keep calm and take things slowly.
Just because you are having trouble booting does not mean you have lost any information on your hard disk.
You may have lost access to it in the way that you are used to, but your operating system and all your information are still there (in 99.999% of cases).

Chances are, Super Grub Disk will be able to either fix your problem for you instantly, or at least boot your operating system for you so you can fix the problem yourself after that."

Good luck.

---

### Post by inversekinetix on 2007-11-26
if you bought a system with XP preinstalled on it you are entitled to 1 disk version of windows.  Them putting a restore version on a hidden partition is beside the point,  demand a disk from your vendor.

---

### Post by travismh on 2007-11-27
UPDATE: Ubuntu is working fine now; I had to manually edit the partition, redirecting the entire installation to my primary drive, as suppose to the default option which installs the swap file into your logical.

thanks again.

---

### Post by bw44 on 2007-11-27
> **travismh said:**
> UPDATE: Ubuntu is working fine now; I had to manually edit the partition, redirecting the entire installation to my primary drive, as suppose to the default option which installs the swap file into your logical.

thanks again.

Didn't quite understand your solution, but I'm glad it worked out!

---

### Post by inversekinetix on 2007-11-28
> **bw44 said:**
> Didn't quite understand your solution, but I'm glad it worked out!

I think he edited the grub menu to make it point to the right hd.  If there is any problem at all during boot with grub it resets the bios on my mb and grub wont load, i have to edit the menu.lst file to get it working again.  Its a real pain

---

### Post by bw44 on 2007-11-28
> **inversekinetix said:**
> I think he edited the grub menu to make it point to the right hd.  If there is any problem at all during boot with grub it resets the bios on my mb and grub wont load, i have to edit the menu.lst file to get it working again.  Its a real pain

Thanks, but I think there's something I don't understand.  Maybe you can help.  I  thought GRUB was installed to the MBR and if that was damaged, you had to restore it so that it pointed to a working OS. Since the Ubuntu install failed in this case,  I though he would have to restore the MBR to point to the Windows partition.  When you say that GRUB resets the bios, what do you mean?  I thought GRUB just pointed to the partitions where bootable OS's lived. If there's a problem then the bios is reset to point to the "default" hard drive?  

If you could explain this a bit further I'd appreciate it.

---

