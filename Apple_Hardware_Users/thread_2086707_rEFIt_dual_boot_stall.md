---
title: "rEFIt dual boot stall"
date: 2012-11-21
forum: Apple Hardware Users
---

### Post by GraphiXS6 on 2012-11-21
Hello, new here.  So, I am not a huge fan of mac, but unfortunately at my school we have to have them.  So, I decided to dual boot ubuntu.  Now, I burned an image of it onto a dvd after installing rEFIt.  I also created a partition for it, trying several different formats.  So, what happens is, I put the disk in, restart my computer, see the linux icon, press enter on the linux icon.  Then it just goes to a black screen with a blinking text input.  that's where it stops.  It doesn't do anything else (and trust me, I've waited), and it won't let me type.  Just nada.

---

### Post by zaebo on 2012-11-22
I had the same problem, though using an USB stick, last saturday when trying to install xubuntu 12.04 amd64+mac version. Simply doesn't boot for me.
Then I tried the normal xubuntu 12.04 amd64 version and I was able to boot and install.

I don't know which version you tried, and if this is the right way to proceed. 
But it worked for me.

---

### Post by GraphiXS6 on 2012-11-22
Well, I'm using ubuntu 12.1 32bit.  I'd really prefer to use that, not to mention I don't have any more disks to burn to.  :redface:

---

### Post by zaebo on 2012-11-22
Ok.
But, when it is not possible, maybe you want to try the
amd64+mac or, when that is also not possible (in my case; neither 12.04 nor 12.10 possible), then the amd64 version.
At least when installing in EFI mode, the version of your EFI ( >= core 2 duo should be 64bit (?) ) should match the OS, when I remember right.

---

### Post by GraphiXS6 on 2012-11-22
Maybe I'm not getting you, but I only know of a "normal" version of ubuntu.

---

### Post by zaebo on 2012-11-22
There is a "special" Mac version of Ubuntu 64bit.
If I understand good, the difference of this version is, that it only runs in one boot mode, legacy I think, whereas the "normal" version offers two boot modes, to be bootable under BIOS and UEFI. The EFI of mac's seems to have a problem with that.
(Also I have a problem with the mac version).

But should be only available for the 64bit Ubuntu.
You can check it out here:
[http://www.ubuntu.com/download/desktop/alternative-downloads]("http://www.ubuntu.com/download/desktop/alternative-downloads")
under 'Other Images' and select a mirror.

---

### Post by GraphiXS6 on 2012-12-03
Well, I'm back.  I tried the 64amd+mac precise pangolin, and that didn't work.  That and I've already tried the "normal" desktop ubuntu.  Before I burn my 4th 2 dollar dvd, what should I use?  The alternate amd64+mac?  The powerpc, though I don't think this laptop is powerpc?  No matter, here's my system if that helps. 

2.5 GHz Intel Core i5
4GB 1600 MHZ DDR3
Intel HD Graphics 4000 512 MB
OS X 10.8.2

and, again, I'm using rEFIt.

---

### Post by GraphiXS6 on 2012-12-04
Actually, a quick thought, should I try 12.10?

---

### Post by trogdor1138 on 2012-12-05
Personally, and maybe this is heresy around these parts, but I would recommend forgoing rEFIt/rEFInd altogether. You don't need it; it's a boot manager that provides some extra features that are sometimes useful. It's not a boot loader.

The correct image for you depends on your ultimate goal. If you would like to use EFI mode, you want the regular desktop image. If you want to use BIOS mode (Boot Camp) you'll want the special Mac image. Either one, I would definitely recommend the 64-bit (amd64, even on an intel processor) version.

If none of the above really makes sense:

- Get the special Mac version: [http://releases.ubuntu.com/quantal/ubuntu-12.10-desktop-amd64+mac.iso](http://releases.ubuntu.com/quantal/ubuntu-12.10-desktop-amd64+mac.iso)

- Remove rEFIt from your Mac

- Burn the image to a DVD

- Reboot with the disc in, hold option when you hear the chime, then select the "Windows" disc

- Install Ubuntu as normal

I would definitely recommend using 12.10; the included 3.5 kernel includes some modules that make initial setup much easier. I'm using 12.10 on my MacBook Pro 8,2 and I've had no problems.

---

### Post by GraphiXS6 on 2012-12-05
Okay, forwent the rEFIt with one of my old disks (haven't tried one you sent me yet) and I got the same black screen with blinking cursor.  Do I need some BIOS thing in my drive similar to how there's an efi folder in the drive for rEFIt?

---

### Post by GraphiXS6 on 2012-12-05
Well, I've tried all of the above.  Still the black screen.

---

### Post by trogdor1138 on 2012-12-05
No, you don't need to manually set up BIOS emulation; it "just works."

What happens when you actually boot and hold option? You should be seeing the built-in boot selector, and not rEFIt. After your Mac queries the drives, you'll see a CD icon labelled "Windows" and this is what you want (Apple's firmware labels all BIOS OS's Windows).

Are you able to get that far? A blinking cursor would generally indicate bad media; did you check the md5 hash for the image before burning it?

It's common to need to tweak kernel parameters to actually boot into Ubuntu on a Mac, but you should be seeing a GRUB menu at the least.

---

### Post by GraphiXS6 on 2012-12-07
Yeah, I did all that.  My friend and a sort of techy-guy took a look at the disk contents and said it looked alright.  But, yeah, just a blinking cursor.

---

### Post by este.el.paz on 2012-12-10
> **GraphiXS6 said:**
> Okay, forwent the rEFIt with one of my old disks (haven't tried one you sent me yet) and I got the same black screen with blinking cursor.  Do I need some BIOS thing in my drive similar to how there's an efi folder in the drive for rEFIt?

Homes:

The scenario you are describing is a tad confusing, the rEFIt app is good if you are trying to run a dual boot system on a Mac.  I've got a dual boot OSX and Linux Mint Mate 64 bit system running on a 2010 MBPro, and I've done a fair number of installations because of issues with GRUB . . . rEFIt is there to allow you to select either OSX or Linux, but AFTER the Linux system is installed . . . it seems like you might be trying to select it, prior to installing???  Best to have OSX and rEFIt installed, then after burning the DVD on the "slowest speed possible" . . . install DVD and boot while holding down the "C" key . . . and that should boot the DVD . . . follow instructions.  If you get the rEFIt window, then you would want to select the DVD symbol to boot the install DVD . . . there was a suggestion on some thread to use the Ubuntu installer with GParted to partition the portion of the disc you want for Home, Swap, and boot . . . flag as such, then stop the installer, boot rEFIt and use the "synchronize" function of rEFIt to synchronize the partitions, then restart the installer and when you run the installer it will then recognize where to put GRUB, otherwise it might be a problem . . . that issue was a factor in the LM installation, which uses Ubuntu and Debian, don't know if straight Ubun there are issues with getting GRUB set up.  Good luck.

e.e.p.

---

### Post by milan475 on 2012-12-11
Here's what I know:

- Ubuntu 12.10 (not the +mac) 64bit iso can be booted in ISO mode. An USB stick or DVD will appear as "EFI system" or something like that when pressing alt (option) at boot. Then u can just proceed installing ubuntu. That's what I've done.

- Ubuntu 12.10 32bit or the +mac 64bit version will only boot in BIOS emulation mode. An USB stick will not work. If u burn it to a DVD it should appear as windows when pressing option at boot. Then u can just proceed installing ubuntu.

No refit was needed for me, but maybe u can try to sync mbr tables and see if that works?

Good luck! 

BTW. You can try to install in efi mode and convert to BIOS emulation mode afterwards.

---

### Post by GraphiXS6 on 2012-12-17
Since there seems to be confusion, I un-installed/got rid of rEFIt.  Then, I boot up with the disk in while pressing alt.  It gets to the screen with all the boot options.  I choose the "windows" disk, which is actually my ubuntu disk.  It loads on that for a while then goes to a blank black screen with a blinking text input similar to that in a terminal.  It stays that way forever.  So, I tried going into my Ubuntu virtual box, plugged in a pendrive, then made a bootable usb.  Then, I boot back up doing the same as the disk, except with the pendrive in.  I select the "windows" flashdrive icon and it loads for that for a second, then goes to the black screen, displays a lot of text fast, then says "[boot error]".  And that's where I am.

---

### Post by GraphiXS6 on 2012-12-30
I try not to do this, but any thoughts?

---

### Post by curtistuckr on 2012-12-30
I installed Ubuntu 12.10 (i386 32-bit) on a Mac mini (Mid 2011). I had an issue where the Mac would not boot from the DVD that I had burned using OS X Disk Utility. I did an SMC reset on the Mac. Honestly, I don't know if that "fixed" it but I was able to boot from my optical drive after that.

I used rEFIt during the installation but I have since removed it. It's only been a couple of days but, so far, the only real nagging problem I've had is getting Ubuntu to "see" my Bluetooth keyboard and pointing device. This was solved by plugging in USB versions of both.

---

### Post by clumsyNInja on 2012-12-30
Have you checked out the wiki for running Ubuntu on MacBooks? It may have some specific instructions, also check out the generic install guide here [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) especially the part about fixing the partition table from rEFIt (I know you said you uninstalled it but in my experience it is the easiest way to get everything working) 

Here is the link to the MacBook wikis [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

EDIT: Oops looks like I misread the OP. Have you tried verifying the disk in another computer? And by that I mean actually booting from it, you said your friend looked at it but did it actually boot?

---

### Post by curtistuckr on 2012-12-30
I agree with clumsyNinja in that the generic install guide is the best place to start in getting Ubuntu on the machine and running. But if you can't get the machine to boot from CD/DVD you're kind of dead in the water. If an SMC reset doesn't work try to boot from an external optical drive. I'm using an Apple SuperDrive (since my Mac mini didn't come with an internal optical drive).

---

