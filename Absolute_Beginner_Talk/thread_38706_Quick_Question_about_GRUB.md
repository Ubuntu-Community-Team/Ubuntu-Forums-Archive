---
title: "Quick Question about GRUB"
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by davidmigl on 2005-06-01
Hello all,

I recently added another HDD, and with it, Ubuntu to my primary machine.  I installed GRUB and am happily dual booting now.

One thing still leaves me thinking, however.  My first HDD in the boot order is the one that WinXP is installed on, and when I boot to that HDD, I get the GRUB boot loader.  So it would be safe to assume that GRUB is installed on the WinXP disk, right?  (I did install it to the MBR.)

I changed some settings in /boot/grub/menu.lst to make it where XP was loaded by default.  This was what got me thinking.  GRUB is installed on one HDD, and it loads its settings from another.  

?!?!?!?!?!?!?!?

What if I format that partition?  How could I edit the GRUB boot menu?  What if I removed the HDD completely?  Would I still be able to edit GRUB, or at the very least would it be able to run?

I guess I had a quick answer to the next-to-last question the other night as I was tidying up some cabling.  The power cable for the Ubuntu disk came loose, but i didn't realize that until the computer got to "Detecting IDE drives" in the BIOS startup, detected all of them minus the Ubuntu drive, and then refused to go any farther.  Perhaps this was because the drive was plugged in but not powered up?  Or is this what would happen if I removed the drive?  Is my computer tied to this drive for life, and unable to boot without it??? :|

The last question remains unanswered, but I plugged the HDD back in and the machine booted right up to GRUB.  I guess I'm running fine right now, but the unanswered state of this question still leaves me a little uneasy.

---

### Post by betrayed on 2005-06-01
well you if you lost that harddrive and wanted to get back into windows there are many ways of wiping the mbr and it will default boot back into windows

---

### Post by davidmigl on 2005-06-01
[QUOTE=betrayed]well you if you lost that harddrive and wanted to get back into windows there are many ways of wiping the mbr and it will default boot back into windows[/QUOTE]
 I guess you'd be right.  I unplugged the IDE cable and the power cable, and I got GRUB error 17, which is to be expected.  I assume that if I ever removed that HDD, I could just boot off an XP CD into the Recovery Console and type 'fixmbr', right?

Now for a less extreme question: what if I uninstalled Ubuntu by formatting the partition?  I'd still get the error, since the GRUB config files were stored in Ubuntu, right?

---

### Post by poofyhairguy on 2005-06-01
[QUOTE=davidmigl]
Now for a less extreme question: what if I uninstalled Ubuntu by formatting the partition?  I'd still get the error, since the GRUB config files were stored in Ubuntu, right?[/QUOTE]

Yep. You need to redo that part of your harddisk.

---

### Post by betrayed on 2005-06-01
I can say this is also a feature I like though.  I decided to test fedora core on a slice of my harddrive well i wasn't paying attention and it redid my mbr.  If I had just lost the grub config it would have sucked as i have the machine set up in a triple boot with ubuntu, gentoo and freebsd and ubuntu with a couple of different kernels.  But because the config was on the drive with ubuntu I just reloaded it and I was back where I started.

---

### Post by NemanjaM on 2005-10-03
I am in a situatin very similar to this one.

I had xp installed on smaller(master) disk and after that I decided to try out linux. I installed it on much larger disk, which is set to slave by jumpers. 

If I remember correctly during installation I set grub to boot from xp disk, as he would not accept booting from linux disk.

Now that I have mostly set up my linux I wish to format xp disk and give it a fresh install and continue using it, but this time with no internet connection, i.e. no viruses. I am afraid that by doing this I will compromise, if not tottaly ruin the chance to boot up ubuntu the way I just made it.

Is there a program from which I can manually change booting partitions(and graphically if possible), maybe even create a boot disqete(it is more attractive solution than having to reinstall ubuntu all over and once more collect all the packages)? A friend of mine,once running mandrake10 had that kind of program, I don't remember the name, though...

Thanks for listening..

---

### Post by casper_2095 on 2005-10-09
>  Is my computer tied to this drive for life, and unable to boot without it?
Yes. And no.  I could be wrong I'm just going from memory on some fiddling around getting raid going a couple of weeks ago.  It looked a bit to me like grub does a two stage bootstrap. The first stage is installed in the mbr, but that calls a second stage which is found in the /boot directory.  So for grub to go all the way the /boot directory (or whereever the second stage is) must be on the same disk.  You could create a tiny little partition for the /boot directory and all the myriad kernels and oddities you want to bootstrap.

> create a boot disqete?
Is this relevant for you?
[http://www.tldp.org/HOWTO/Bootdisk-HOWTO/]("http://www.tldp.org/HOWTO/Bootdisk-HOWTO/")

---

### Post by zerhacke on 2005-10-09
[QUOTE=davidmigl]I assume that if I ever removed that HDD, I could just boot off an XP CD into the Recovery Console and type 'fixmbr', right[/QUOTE]
Not if you have XP SP 2.  You won't be able to boot the drive and fixmbr or fixboot with SP2.

Yet another fix by Microsoft that gums more up than it fixes.  If you dual boot and even remotely think you may ever change bootloaders again, don't install SP2.

If you have installed SP2 already and wish to remove grub you can uninstall SP2 (the exact procedure has been forgotten by me but can easily be found by googling) by booting to windows, uninstalling SP2, then installing the Recovery Console to your hard drive.  Reboot, start the recovery console, then fixmbr.  It'll destroy grub and give you back the Windows bootloader, at the cost of making your Linux disk not bootable.  You can then optionally reinstall SP2 after booting to Windows.

I had to do this once when removing the drive that housed Ubuntu that had gone bad.  Luckily for me the drive held out long enough for me to perform the above operation.

---

