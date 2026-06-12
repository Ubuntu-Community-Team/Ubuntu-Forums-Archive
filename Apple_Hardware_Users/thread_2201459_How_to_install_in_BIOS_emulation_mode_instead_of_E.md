---
title: "How to install in BIOS emulation mode instead of EFI?"
date: 2014-01-24
forum: Apple Hardware Users
---

### Post by timo-wiren on 2014-01-24
I'm using a 2010 MacBook Pro with Nvidia 320M. The proprietary driver does not work in EFI mode and only shows a black screen (not even backlit). This is a common problem. How do I install or boot Ubuntu in BIOS emulation mode? I can dedicate the whole HDD to Ubuntu, no need for dual boot.

---

### Post by baabsaget on 2014-01-24
I assume you have rEFInd/rEFIt installed

When installing ubuntu, go to the section where you select what part of the disk to use and hit "Something Else"
Create two partitions, setting the first one to be used as an ext4 filesystem. This will be your root partition, and it will store all your data. make sure you make it large enough. set the mount point as "/". The second partition will be used as swap. Set its size to at least as much as how much RAM you have. Set it to be used as a swap area.  There should be a drop down box marked "location for bootloader". MAKE SURE you set it to the partition you marked as "/". After that, continue the install as usual. 

When you hit the linux/ubuntu icon in rEFIt, you will have to wait ten seconds before GRUB shows up.

---

### Post by timo-wiren on 2014-01-27
I got the BIOS emulation and Nvidia driver working by installing from a DVD instead of from a USB stick.

---

### Post by Julien Dutant on 2014-03-01
I have the same issue but not CD/DVD drive. I'm still looking for a solution but struggling. Any suggestions?

I followed the instructions here: [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode) but without luck. (I've created a bios_grub partition; the current ubuntu 13.10 install from Live USB doesn't boot. When I run boot-repair from live USB, it warns me that "The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating an EFI partition...". I ignore it; but after a bit of processing the message reappears, and so on, so boot-repair never completes. 

(Here is the boot-repair diagnosis: [http://paste.ubuntu.com/7018019/](http://paste.ubuntu.com/7018019/) . It looks like core.img should be in the bios_grub partition but isn't. I've tried a reinstall placing the bootloader in that partition, but the result is the same: [http://paste.ubuntu.com/7018379/](http://paste.ubuntu.com/7018379/).)

Note: I haven't tried [**[COLOR=#000000]baabsaget[/COLOR]**]("http://ubuntuforums.org/member.php?u=1802277")'s solution. It looks like the Ubuntu live USB only install EFI versions of GRUB/Ubuntu, so I don't see how it could work. (I don't have rEFInd and I don't have the OS X on the laptop. It looks tricky to install it from linux without breaking Mac firmware.)

---

### Post by d4m1r on 2014-03-11
1) Lots of reasons NOT to have a swap partition when installing Ubuntu on a Macbook so I'd advise against it. The main reason being the 4 logical NTFS partition limitation. Also, you will get better performance if you don't use swap if you have 8GB of RAM in your Macbook anyway (depending on usage but general rule). If you have 4GB or less RAM, having a seperate SWAP partition might help your performance but I'd still recommend against it because this is all already fairly difficult to get running correctly off 1 HDD using rEFit/rEFind.

2) To install Ubuntu on a Macbook in BIOS emulation mode instead of EFI, simple have the Ubuntu install CD in the Macbook and while it is booting, press and hold the Alt (IIRC) button. You should be taken to a separate boot screen where the Ubuntu CD should come up twice, once for the BIOS installer and the other for the EFI installer. Select whichever one you want. Ubuntu 12.04 LTS and beyond (IIRC) have support for both but default to EFI if the computer supports it I believe...

Hope that explains it :)

---

