---
title: "install problems.. please helppp"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by aledelic42 on 2007-01-18
im pretty new to linux and i dont know what to do..
im trying to put ubuntu 6.10 edgy on my computer that i just built (core 2 duo e6300,  ECS P965T-A motherboard, 320gb sata hd, 1gb ddr2 ram, 7600gt)
when i try to enter Start or install Ubuntu a screen comes up with..

[17179573.404000] PCI: JMB36x: Enabling dual function on 0000:03:00.0
[17179573.428000] PCI: Cannot allocate resource region 0 of device 000:03:00.0
[17179573.428000] PCI: Cannot allocate resource region 2 of device 000:03:00.0
[17179573.428000] PCI: Cannot allocate resource region 3 of device 000:03:00.0
[17179573.428000] PCI: Error while updating region 000:03:00.0/0 (0000c00 !=00000000)
[17179573.428000] PCI: Error while updating region 000:03:00.0/2 (0000c08 !=00000000)


the same thing comes up when i start ubuntu in safe graphics mode and check cd for defects
same exact thing with my kubuntu disc too..

hopefully someone can help

---

### Post by kebes on 2007-01-18
Unfortunately the motherboard you selected has an Intel 965 chipset, which has some issues with Linux. Specifically the 2.6.17 kernels and older don't work well with it. This is fixed in the newer kernel ( 2.6.18 ), which ships with Fedora Core 6, the current OpenSUSE, and will be included in the next version of Ubuntu (Feisty Fawn).

For more information, see here:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)


So unfortunately installing Ubuntu Edgy will not be a super-simple process with this motherboard. Your options are:

1. Refer to the above thread, where numerous work-arounds are described. The exact work around depends on a number of factors, but there are lots of things to try. For instance often the problem has to do with installing from an IDE CD/DVD drive. You can try installing from a USB key or SATA CD-ROM perhaps. There are also kernel boot options (such as "all-generic-ide") that help overcome this problem. If you go this route, you can post problems you encounter along the way, and we will help.

2. You could try to install a different version of Linux, which includes the newer kernel. As I said, Fedora Core 6 and OpenSUSE have a newer kernel by default. (Note that if you manage to get Ubuntu installed you can upgrade to the newest kernel anyways... you just have to install somehow!)

3. You could try using one of the highly experimental development CDs for the next version of Ubuntu (Feisty Fawn):
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
The daily images should include the newer kernel... but this is very much unstable software so it might be a bad choice if you want a stable machine at the end.

It may be possible, however, to boot into a LiveCD session using the Feisty CD, but then to actually install the Edgy version of Ubuntu. (Does anyone else know how to dowgrade from a Feisty to an Edgy install?)


I'm sorry that the news is not great, but we're here to help if you want to go ahead and attempt this installation.

---

### Post by aledelic42 on 2007-01-18
i see..
well thank you very much for that information
i guess ill try fedora core 6 then


thanks

---

### Post by aledelic42 on 2007-01-18
this is probably not the right place to post this but im trying to set up a dual boot with fedora core 6 and its not recognizing my hard drive
do you know how i could fix this

and by the way im trying to dual boot with windows xp pro

---

### Post by kebes on 2007-01-18
> **aledelic42 said:**
> this is probably not the right place to post this but im trying to set up a dual boot with fedora core 6 and its not recognizing my hard drive
do you know how i could fix this

Can you be more specific? Does the installer load and but when you get to disk partition it says it can't find any disks? Or Does the installer not even boot properly, and issue some errors related to disks? If you can copy down the exact error message, that would help.



When I was trying to install Ubuntu Edgy on an Intel 965 chipset, I had to eventually use Fedora Core 6 instead. The details of my efforts are in this thread:
[http://www.ubuntuforums.org/showthread.php?t=301529](http://www.ubuntuforums.org/showthread.php?t=301529)

The short version is this:
I installed FC6, but instead of doing a normal install, at the beginning of the installer I had to set some extra options (kernel boot parameters). The ones that worked for me were:
linux text all-generic-ide pci=nommconf irqpoll

However it may depend on the exact motherboard. You can try various combinations of these kernel options:
all-generi-ide
pci=nommconf
irqpoll
noapic
nolapic

In particular the "all-generic-ide" might help resolve a conflict when it comes to recognizing drives.


Hope that helps...

---

### Post by aledelic42 on 2007-01-18
linux text all-generic-ide pci=nommconf irqpoll
thanks that one worked for me too :D 

my problem was that the installer would start up and i would try to install it and then it would go through some things and then after i picked the language it would take me to a window with partitioning options but wouldnt have any hard drive to choose..
now it seems like its working right i just have to hopefully set this all up correctly
thanks very much for the help


EDIT:
well this is harder than i thought.. do you think youd be able to give me a link to a site with detailed instructions to partition and dual boot fedora core 6 or tell me or something.. i dont know what to put in the mount point or file system type or anything really =/

thanks

---

