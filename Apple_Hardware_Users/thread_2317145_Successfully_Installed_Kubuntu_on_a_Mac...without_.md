---
title: "Successfully Installed Kubuntu on a Mac...without rEFIT?"
date: 2016-03-13
forum: Apple Hardware Users
---

### Post by emily11 on 2016-03-13
Hi everyone, I'm new to the forums but not so much to Linux. So I have this really old Macbook Pro mid 2009 that for some time was dualbooted with Yosemite and Windows 7, but since I usually used Windows 7, I decided to give Windows 10 a try. Well, Microsoft sent out [a faulty update]("http://www.forbes.com/sites/gordonkelly/2015/08/08/windows-10-forced-updates-causing-endless-crash-loop/#2a527355181f") and I caught it and it totally screwed my computer up, both partitions. Frustrated, I just threw in an old Windows 7 disc and reformatted the entire drive. Windows worked just fine without Bootcamp and I just installed the necessary Bootcamp drivers from my Apple disc. Then it got really slow again, but I got a new computer by that time and this one was just sort of useless. So I decided to give Kubuntu 15.04 a shot with it. I was able to install Windows 7 without dualbooting. Why wouldn't Kubuntu work the same way?

So when I put the disc in and restarted it, I held down C and it booted the Kubuntu installation. I still had no idea if once it was installed, it would get past a GRUB command line. But it rebooted just fine. Sound is working, video is working, it responds to key shortcuts. All I have to do is get Broadcom drivers and nVidia drivers. 

So I have no problem with the installation or the OS itself. My question is, how did this happen? I thought the only way to install Linux on a Mac was if I had rEFIt or rEFInd or had some sort of dualbooting option. But now Kubuntu is my primary OS without a hitch. I'm hoping someone with greater knowledge than I have will be able to figure out what went right with this machine. I'm able to answer any questions anyone has.

---

### Post by Bucky Ball on 2016-03-13
Welcome. Seems pretty straight forward from here, but I could be wrong. As you are only installing Ubuntu on the machine you don't need to cajole, massage, trick and cheat any other bootloaders used by Win or Mac and round them up with refit so they work happily together. Generally why you need to jump through hoops with things like refind/refit/bootcamp and all that from what I understand.

If you have a dig around online you'll probably find some clues ...

* [Found this]("http://askubuntu.com/questions/42711/how-to-install-ubuntu-as-the-single-os-on-a-macbook") in less than a minute. I see no mention of refit/refind.

---

### Post by ineuw on 2016-03-14
It seems that recent versions of the Ubuntu family (in my case Xubuntu 14.04) install on old MacBooks (version 3, 2007 Intel in my case) from a USB drive without any additional software. Xubuntu 14.04  64bit took care of the EFI setup automaticaly and It is what I am using currently to write this post.

---

### Post by emily11 on 2016-03-14
Ah wow this is super interesting because everything I have read previously told me that it couldn't be done without refit. All the times I've tried to install Linux on its own have failed, I didn't get past a command line. In fact when I first started Kubuntu on this, it brought me a command line and I thought that again it didn't work. So I just pressed ESC, thinking it would just restart but it immediately booted the installation.

---

### Post by ingcontiingconti. on 2016-04-04
I have yet finished to install on a Mac Pro. (the cylinder...) ubuntu 15.


No need to use refit.
I installed from USB stick without any boot manager.
If you do not use a bot manager (not a boot loader..) your mac will simply boot in ubuntu.
Using "ALT" key you will be carried to usual choice of disk, but you cannot see a Ubuntu disk.
So If You are in this situation, is fine.
recap:


1 to boot in OSX/windows:ALT at boot
2 to boot in Ubuntu: no key at boot

The ONLY big issue was using my radeon card on boot.
Mac Pro freezes.

I forced mode to "**nomodeset" (**Instructions on ubuntu sites are not so clear..)
 
Anyway after booting from USB, You will have a purple screen with 3 options, but You MUST patch video driver BEFORE installing, otherwise mac PRO will hang.
so use "E" key and add nomodeset in line:

 linux /boot/vmlinuz-linux .... quiet splash **nomodeset**

so it booted.

After installing you must add with feature to the normal boot, too.

So I edited grub file:
sudo nano /etc/default/grub

Adding the same option.
and after: 

sudo update-grub



Now Mac pro works, BUT no wifi, so to enable wifi:

1) connect using ethernet cables (in DHCP, ubuntu recognizes built in Gigabit adapters..)
2) install "Dynamic Kernel Module Support" dkms using:
    sudo apt-get install dkms3) the same for wifi drivers:
     sudo apt-get install bcmwl
from respective sites.

Hope this can help others.

---

### Post by izznogooood on 2016-04-06
> **ingcontiingconti. said:**
> I have yet finished to install on a Mac Pro. (the cylinder...) ubuntu 15.


No need to use refit.
I installed from USB stick without any boot manager.
If you do not use a bot manager (not a boot loader..) your mac will simply boot in ubuntu.
Using "ALT" key you will be carried to usual choice of disk, but you cannot see a Ubuntu disk.
So If You are in this situation, is fine.
recap:


1 to boot in OSX/windows:ALT at boot
2 to boot in Ubuntu: no key at boot

The ONLY big issue was using my radeon card on boot.
Mac Pro freezes.

I forced mode to "**nomodeset" (**Instructions on ubuntu sites are not so clear..)
 
Anyway after booting from USB, You will have a purple screen with 3 options, but You MUST patch video driver BEFORE installing, otherwise mac PRO will hang.
so use "E" key and add nomodeset in line:

 linux /boot/vmlinuz-linux .... quiet splash **nomodeset**

so it booted.

After installing you must add with feature to the normal boot, too.

So I edited grub file:
sudo nano /etc/default/grub

Adding the same option.
and after: 

sudo update-grub



Now Mac pro works, BUT no wifi, so to enable wifi:

1) connect using ethernet cables (in DHCP, ubuntu recognizes built in Gigabit adapters..)
2) install "Dynamic Kernel Module Support" dkms using:
    sudo apt-get install dkms3) the same for wifi drivers:
     sudo apt-get install bcmwl
from respective sites.

Hope this can help others.

Did you re-partition your drive? Or did ubuntu install find your OSX and ask you to install alongside?

---

### Post by Bob_Bruce on 2016-04-10
When El Capitan slowed down my 2009 iMac, I tried Ubuntu with a bootable USB stick made using Unetbootin. When I found Ubuntu worked well, I rebooted with the USB stick and it gave me the option to install Ubuntu, which I did.


When rebooting the iMac the grub menu came up, with Ubuntu but not OS X, so the only way to get back into OS X was to hold the Alt key while rebooting. After that I installed rEFInd (the Refit replacement), which gives you boot options automatically, and things were much easier.


To install from terminal:


sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind


Now I've got a couple Linux distros installed on partitions with OS X in it's original place. Creating a bootable USB stick is really easy in Ubuntu with the "Startup Disk Creator" utility. You could reinstall OS X in a partition if you wanted but with a new system maybe you don't need it.


I've found that when I update OS X it resets the grub loader to go right into OS X as though nothing else in on the drive so I have to boot from a USB stick to reset the grub menu and also uninstall and reinstall rEFInd. 


Installing a new Linux distro also resets the grub bootloader but at least gives me the option to boot into other versions. Unfortunately I still have to uninstall and reinstall rEFInd every time but at least it's quick and easy.

---

