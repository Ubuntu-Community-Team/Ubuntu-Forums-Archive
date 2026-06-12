---
title: "Multiple 'boot from flash drive' situations playing nice together?"
date: 2013-03-08
forum: Any Other OS
---

### Post by opethfan89 on 2013-03-08
Hi all!!

It's been a long time since I've posted, and it's good to see the community still growing :) I have a rather specific question to ask, and although I'm currently using Linux Mint, I felt it appropriate to ask here as its 1) Ubuntu-based and 2) My question is distro-independent (kinda)

What I'm wanting to do is use my 32GB SanDisk flash drive as my go-to diagnostic tool.  Currently, I have a number of tools on there, as far as the PortableApps.com suite of software and a couple of other things that I can't think of right now.  I'd ideally like to include a number of different tools on there, but the issue is that each of these tools (as I understand it) will overwrite the boot record of the drive/re-format it to their specific needs.  So I really need them all to play nicely with each other.

I'm wanting to include all of the following on my flash drive (or, if this isn't possible, even in a bootable external HDD [recently purchased a 1.5TB one on sale at Best Buy])

[LIST]
[*]Katana (of which I only found [one mention]("http://ubuntuforums.org/showthread.php?t=2004980&highlight=katana") after a quick search)
[*]PortableApps.com suite of programs (an aside - is there any way to have access to all the tools without booting into a Windows environment?  I haven't found any indication of such while navigating it)
[*]Hiren's Boot CD, via USB of course
[*]Linux Multi Boot (ala YUMI or UNetBootin, etc)
[*]And perhaps in the future any other suite of tools that I can find that run off bootable USB
[/LIST]

Is my idea just a delusion of grandeur, or is it possible?  I understand the logic behind it, but am not intimately familiar with how MBR's/boot records work under Linux.

I appreciate any help in this task, but would also ask for a mini explanation of what is going on and why so I can gain a deeper understanding and expand my Linux knowledge.

Thanks in advance!!

Opethfan89

---

### Post by Perfect Storm on 2013-03-09
Moved to Other OS/Distro Talk.

---

### Post by oldfred on 2013-03-09
I do not know about your specific applications. Not all ISO can be booted with grub2's loopmount, but many can be.

 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I did it manually before any of the above scripts became available. 
      
 MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sda

And even a flash drive is very similar to a hard drive.
      
 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

With my larger flash drives, I have a full install of Ubuntu and then in additional partitions have more ISO. 
I also did create one smaller flash drive with Windows repairCD, but it took so little room that I installed grub to that flash drive and put a couple more ISO on the same flash drive.

But I am more in the category of if you only have a hammer everything looks like nail. I have grub2, so everything looks like it will boot with grub2. :)

---

### Post by opethfan89 on 2013-03-13
> **oldfred said:**
> I do not know about your specific applications. Not all ISO can be booted with grub2's loopmount, but many can be.

 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I did it manually before any of the above scripts became available. 
      
 MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sda

And even a flash drive is very similar to a hard drive.
      
 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

With my larger flash drives, I have a full install of Ubuntu and then in additional partitions have more ISO. 
I also did create one smaller flash drive with Windows repairCD, but it took so little room that I installed grub to that flash drive and put a couple more ISO on the same flash drive.

But I am more in the category of if you only have a hammer everything looks like nail. I have grub2, so everything looks like it will boot with grub2. :)


Thanks for the response!

I think you repeated a little bit redundant information about things I feel pretty comfortable doing.  My question is very specific, in that I want to have a number of USB-bootable tools all on the same flash drive.

How I understand it is that when I install something, say katana (which is just a security/pentest toolkit, source link is [here]("http://www.hackfromacave.com")), it installs GRUB on the flash drive and then overwrites the MBR.  I can still put other FILES on there, but I can't put another bootable set of tools on there.

Then, there is something like YUMI which would create a multi-boot linux flash drive, which I already have.  But I'd like to combine YUMI with Katana and a few other tools to all be consolidated onto a single flash drive.

Is this task possible to accomplish? I'm hoping for a more specific response to my exact situation.

Thanks,
Opethfan89

---

### Post by oldfred on 2013-03-13
I do not know katana. 

Often the issue of booting a different install is first whether it can directly boot with grub2's loopmount and then which options are required. Usually  inspection of ISO's boot for internal path and boot options is required and then some experimenting with grub boot stanza.

Did you search thru the thread to see if someone had booted katana or tried google to find an example?
If you know what katana is based on, then the boot stanza is usually the same or similar.

I have trouble reading Katana's site, too dark for my eyes, but it looks like it is just another one of the scripts to install many installs and some apps.

---

