---
title: "Bootloaders when dealling with more than 1 linux OS"
date: 2011-05-13
forum: Any Other OS
---

### Post by Tikhon03 on 2011-05-13
I have a laptop and a desktop, each with a similar multi-OS setup.  There is a Primary partition with Windows, and an extended partition.  The extended partition is divided up with one swap partition, several root partitions for different Linux OS's, a data partition, and a recovery partition.  With windows installed first, and then several of the Linux OS's installed, I installed Kubuntu last and used its boot loader grub2 to recognize all operating systems on the drive. 

This setup proves very effective on my laptop which was purchased from Dell, but not on my desktop, which I built from scratch.  The problem is the hardware.  I chose an ATI graphics card that Fedora did not get along with (Radeon HD 5570).  Of course my laptop also has an ATI graphics card, as well as a Broadcom wireless network adapter - not the most linux friendly hardware - but in spite of this every linux system put on it has worked well.  Now there is a driver for the Radeon HD 5570.  When I installed Kubuntu, the driver was easy to install.  With Fedora, it also should have been easy, but required a change to grub.  But I am using grub2, and it is handled by Kubuntu, thus Fedora was not able to find grub.

Now I could probably go into grub2 manually and edit things myself, but this seems kind of ad hoc.  I can easily see why giving all OS's equal access to the boot loader, by having it installed on a boot partition and chain loading, would be a good thing.  But is it possible to do chain loading with grub2?  If it is done with grub2, would an OS like Fedora know what to do with grub2?  If I download the ATI driver and install, Fedora tries to change grub.conf.  If it had access to grub2, would it know that grub.cfg isn't edited directly, and do this by the new approach?

I know that the nvidia drivers tend to be more reliable.  The fedora people seem to be sick of ATI, and really I don't blame them.  But if I replaced the ATI graphics card with an nividia graphics card, I'm pretty sure I would be in the same boat with fedora not having access to grub.  After switching to an nvidia card, Fedora still wouldn't be able to find grub, and so it probably would not be able to install the driver. So basically, I am wondering what is the sanest way to set things up.  Should I try to learn how to do chain loading?  Should I stick with the current boot loader arrangement?  Or is there another option that I am not aware of?  I would very much like some suggestions, before doing anything about the graphics card.  Thank you.

---

### Post by mikewhatever on 2011-05-14
The fact Grub2 handles the initial boot sequence makes no difference for Fedora, because when you select Fedora from the boot menu, grub2 redirects the process to Fedora's grub1. I don't quite follow what was the problem with editing Fedora's grub1 config file.

---

### Post by drs305 on 2011-05-14
> **Tikhon03 said:**
> Now there is a driver for the Radeon HD 5570.  When I installed Kubuntu, the driver was easy to install.  With Fedora, it also should have been easy, but required a change to grub.  But I am using grub2, and it is handled by Kubuntu, thus Fedora was not able to find grub.


I'm not sure I understand the question either, but if you are talking about adding a kernel option to the boot information (such as noapic, rootdelay, etc) this is easily added to the Grub entry for a specific OS's entry. These kernel options are added to the end of the 'linux' line in a Grub 2 menuentry.

---

