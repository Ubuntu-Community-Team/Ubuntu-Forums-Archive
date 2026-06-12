---
title: "Need Advice on Best Distro for my needs?"
date: 2007-09-12
forum: Apple Intel Users
---

### Post by escapedspecimen on 2007-09-12
OK, I have a 15" MBP SR with nvidia card, c2d, etc... 

I love ubuntu and have it running great in VMware. I am currently dual booting OSX and Vista. 

I do not want to alter my MBP with reFIT, etc, beyond the point of restoring it to factory default. 

Thus, I want to run a linux distro off an external HD, it is Firewire or USB. (can choose either)

Can anyone suggest the best distro for INTEL MBPs that can OOB run from external firewire. 

I am very new to linux and am not too knowledgeable when it comes to it. 
From what I gathered it is possible, but a real ordeal to get ubuntu going off an external. I got it installed on my firewire but can't boot it...

So, to recap: a distro that boots from firewire, supports MBP, NVIDIA, etc...  

Sorry if this is in the wrong section, but I thought being on an intel MBP was appropriate. 

Thank you for your advice. 


P.S. If ubuntu could figure out how to make it work easily it would be perfect for me as well as thousands and thousands of INTEL mac users...I heard YDL has figured it out, but I have no idea how that is for INTEL MBPs.

---

### Post by shynko on 2007-09-12
you shouldn't have much trouble with a nvidia graphics card though I'm quite new to this to and am unsure  of ubuntus mac support. But good luck with whatever you choose

---

### Post by slira on 2007-09-12
Hi
I have a ubuntu dapper drake running on a external usb disk. The only thing I had to be careful about was to have NOTHING in that disk before installing. Using the dapper drake installer I made manually a boot (100Mb), a swap (1,5xyour RAM), a root (at least 5 Gb) and a home (whatever you want) partitions (this order) and ubuntu installed and runs perfectly! (recognized all my hardware) 

To boot; I changed my bios, so the first boot device is the external usb disk (when it is turned off, the boot goes directly to the main hdd (internal). When the usb disk is on before booting, grub asks if I want to boot linux (external usb disk) or windows (in the internal hdd). You cam customize your grub by editing menu.lst. 

If your bios does not support this, you can press f11 (or whatever in your machine) during booting to access the usb external and boot from there.

After first booting, from ubuntu or with a partition manager from windows, you can decide what to do with the rest of your usb disk: I did a FAT partition, that I use both from ububtu and windows.

hope it helps; anything else, just post.
slira

---

### Post by alephsmith on 2007-09-12
At this time you will have nvidia problems irrespective of distro.

Until nvidia release an updated driver with OTB compatibility with your laptop you will be forced to patch the driver or use one of the other two documented hacks to get 3D acceleration.
I don't know how long it'll take to integrate the new driver in to ubuntu's nvidia-new packages.

As for rEFIt, I don't think it makes any changes to your laptop other than adding a fancy boot menu. Nothing that a factory reset wouldn't fix anyway.

---

### Post by entangled on 2007-09-12
Still not quite a straight answer because I am using Intel Mac Mini not MBP, and USB not FW. 
I have an external USB drive that I set to MBR (using MacOS DiskUtility). Booted off live CD, partitioned sdb (the external) and installed Ubuntu 7.04 onto external.
It comes up at boot using rEFIt. Just choose it and it boots. I think rEFIt is worth installing. It may even be necessary with a MBR disk?

---

### Post by escapedspecimen on 2007-09-12
I appreciate all of your responses and advice. Like I said I love ubuntu, intalled feisty on my external, 
I just can't boot...

I have searched and searched and all I found is more posts with no resolution. 

I can't edit bios on a MBP with EFI...

also, as far as rEFIT goes, I have never heard of a "factory reset" on a mac. And I don't want to mess with the firmware...My understanding is it is burned into the firmware, altering the boot parameters...Anything that permanent scares me...Then I'm stuck depending on an unsuported bootloader for the future. 

Feisty works just fine in VMware, the main reason I wanted to load ubuntu for real was to have all the functionality, which includes, among other things 3d acceleration, but I guess from what others are saying its not quite there yet. Funny, when I was buying this MBP everyone in these forums told me Nvidia would be cake...

Guess untill it gets a little more usable I'll hold off. I'm, really dissapointed though, booting off an external drive should be a simple thing...

Its probably my lack of knowledge with linux, but it seems like you have to jump through soo many hoops, just to get up and running...kinda makes the newcomer feel more alienated then I already feel.

Thanks Again, and keep the advice coming if anyone has some other ideas...

---

### Post by cyberdork33 on 2007-09-12
> **escapedspecimen said:**
> also, as far as rEFIT goes, I have never heard of a "factory reset" on a mac. And I don't want to mess with the firmware...My understanding is it is burned into the firmware, altering the boot parameters...Anything that permanent scares me...Then I'm stuck depending on an unsuported bootloader for the future.

rEFIt is not a bootloader. It is basically a GUI to use Apple's EFI the way you want to. There is nothing "permanent" about it. [http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

> Guess untill it gets a little more usable I'll hold off. I'm, really dissapointed though, booting off an external drive should be a simple thing...It is more of an issue with the Mac's EFI rather than Linux.

> Its probably my lack of knowledge with linux, but it seems like you have to jump through soo many hoops, just to get up and running...kinda makes the newcomer feel more alienated then I already feel.Well, you are trying to run Linux on hardware that does not support Linux... You have to expect jumping through hoops. If you want a fully functioning, easy Linux machine, get one with fully compatible hardware.

BTW, nvidia, for the most part is well supported by linux. Again, it is the nvidia card of the Mac that has issues. Hopefully, as time goes on, Linux can work around the issues that currently give problems...

---

### Post by alephsmith on 2007-09-12
> **escapedspecimen said:**
> also, as far as rEFIT goes, I have never heard of a "factory reset" on a mac. And I don't want to mess with the firmware...My understanding is it is burned into the firmware, altering the boot parameters...Anything that permanent scares me...Then I'm stuck depending on an unsuported bootloader for the future.

By 'factory reset' I mean: format drive and reinstall OSX.

I just did it last week. Absolutely no trace of rEFIt left.

I have to agree with cyberdork, if your not willing to jump through a couple of hoops then Ubuntu isn't right for your laptop at this time.

---

### Post by escapedspecimen on 2007-09-13
Thanks again for clearing up rEFIt. That is excellent to know it is not permanent! I will give it a try. 

Where I am comfortable on OSX and Vista, linux is very new to me, so I can't justify buying a dedicated "compatible" linux machine, but thought ubuntu was able to run on most intel macs with ease, my missunderstanding...

I will format the drive MBR and try it with rEFIt, to see if I can get it to boot. 

I have mostly been trying the same thing with apple's; option while booting, and "startup disk" preference panes with no luck...

Is it worth it to try with rEFIt or do you think it just won't happen regardless on a firewire disk?

Also, I have been just partitioning a root partition and swap partition for ubuntu. 

Do I need a boot partition to do this or is root good enough? 

Thanks again for the help//and replies

P.S> don't get me wrong, I don't mind jumping through "SOME" hoops and understand a learning curve is inevitable, but this has been a big ordeal to get up and running...

---

### Post by escapedspecimen on 2007-09-13
OK, got refit running, have the Firewire external installed with a root and swap partition.

I get the penguin in rEFIt, but I get a GRUB HARD DISK error on boot

Any suggestions?

---

### Post by cyberdork33 on 2007-09-13
> **escapedspecimen said:**
> OK, got refit running, have the Firewire external installed with a root and swap partition.

I get the penguin in rEFIt, but I get a GRUB HARD DISK error on boot

Any suggestions?
Although the above post mentioned having Ubuntu working on an external drive, I have not seen anyone else have any luck accomplishing that. The emulated BIOS and MBR of your Mac is only capable of booting legacy OS partition that are one of the first 4 on the disk (this is due to the legacy of MBR partitioning, and am not going into here). The method that does seem to work, is creating a small (~100MB) boot partition on the main hard drive (as one of the first 4 partitions) that rEFIt / The Apple bootloader can actually boot from, and then the system will mount the root filesystem and continue on.

---

### Post by Bothered on 2007-09-13
I think your bios needs to support firewire to be able to boot from an external firewire hard disk. If it doesn't support this, you may be able to install onto the firewire drive (the ubuntu installer *can* access the firewire drive) and then subsequently be unable to boot from it (the bios can't). I had this problem in my first ever install of linux.

---

### Post by escapedspecimen on 2007-09-14
Ok, I gave up and installed everything on the internal...Everything seemed to go great, except 1 problem...

rEFIt shows the 3 systems, osx boots, vista boots, and ubuntu starts to boot, but then a scen comes up with:

Ubuntu kernal 2.6.20-15-generic
Ubuntu kernal 2.6.20-15-generic (recovery mode)
Ubuntu memtest
etc...

When I try to boot it just goes black...


I remember on the live cd I had to do safe mode and edit the command like this: erase splash, quiet(?) and ad all_generic_ide to solve this problem with booting the CD.

I feel I need to do the same thing here only I don't know which option to choose and which line to edit...

Unless its something else.

Any suggestions?

Thanks again for all the help.

---

### Post by alephsmith on 2007-09-14
Boot into recovery mode.

Then you need to enable the vesa drivers in xorg.conf
Once you have working X session you can then go about installing the patched nvidia driver.

This is documented in the santa rosa thread, which, while long, includes most of the relevant things on the 1st page.

oh... and you need to remove the splash and quiet options from grub.

---

### Post by escapedspecimen on 2007-09-14
OK  I FOUND IT!  WOOOOOOHOOOOOO!!!! I'm up and running my triple booting MBP!!!!! Yaaaay.


Thanks again for all the advice!!!! 
:guitar:

---

