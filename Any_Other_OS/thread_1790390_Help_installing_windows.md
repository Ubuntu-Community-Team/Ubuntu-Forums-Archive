---
title: "Help installing windows"
date: 2011-06-24
forum: Any Other OS
---

### Post by aerofly5 on 2011-06-24
I have a slight dilemma. My computer currently has Ubuntu 10.10 running on it, however I want to dual boot with Windows 7. I don't have any DVDs and my motherboard is too old to support booting off usb devices. I was wondering if there is a way to install windows from an internal drive without having windows alter the boot sectors before hand. Please note that I have about 5 hard drives in this machine, so that may widen the possible solutions

Thanks in advance

---

### Post by trizrK on 2011-06-25
> **aerofly5 said:**
> I have a slight dilemma. My computer currently has Ubuntu 10.10 running on it, however I want to dual boot with Windows 7. I don't have any DVDs and my motherboard is too old to support booting off usb devices. I was wondering if there is a way to install windows from an internal drive without having windows alter the boot sectors before hand. Please note that I have about 5 hard drives in this machine, so that may widen the possible solutions

Thanks in advance
Sorry if i misunderstood your question but if you were asking if you could run windows with a lower priority than ubuntu? If so then install it on a clean drive and set it lower than the drive you have ubuntu on in your BIOS.

---

### Post by NRWlion on 2011-06-26
[COLOR=Navy][FONT=Comic Sans MS]Good Morning every1,

I can understand your dilemma aerofly, but there are several problems which cause some questions.

#1: 
[/FONT][/COLOR]> **aerofly5 said:**
>  My computer currently has Ubuntu 10.10 running on it, however I want to dual boot with Windows 7. 

[COLOR=Navy][FONT=Comic Sans MS]This (normally) should not be the problem. Google will show you several possibilities how to do that. Just be aware that windows will change the Master Boot Record which might be a little conflict with GRUB from Linux.

Btw are you planning to have win7 and Ubuntu on one Harddrive?
[/FONT][/COLOR]
[FONT=Comic Sans MS][COLOR=Navy]#2:[/COLOR][/FONT]
> **aerofly5 said:**
>  I don't have any DVDs and my motherboard is too old to support booting off usb devices.
[COLOR=Navy][FONT=Comic Sans MS]How will you get the installation files? :confused: I mean: downloading from the net is highly illegal [/FONT][/COLOR] 
[FONT=Comic Sans MS][COLOR=Navy]
#3:[/COLOR][/FONT]
> **aerofly5 said:**
>  I was wondering if there is a way to install windows from an internal  drive without having windows alter the boot sectors before hand.
[COLOR=Navy][FONT=Comic Sans MS]You could try to install windows on a Harddrive from another computer the problem would be, that I dont know if GRUB gets into trouble if you simply put a harddrive with an OS into the machine.

[/FONT][/COLOR][FONT=Comic Sans MS][COLOR=Navy]#4:[/COLOR][/FONT]
> **aerofly5 said:**
> Please note that I have about 5 hard drives in this machine, so that may widen the possible solutions.
[COLOR=Navy][FONT=Comic Sans MS]I would not be so sure about it simply because of the doubts described above. there are severals things to remember at a dual boot. And due to the fact that i am not completely familiar with linux and especially with GRUB Bootloader i am not able to help you more than to this stage. 

But anyways I wish you all the Best for your project !
NRWlion
[/FONT][/COLOR]

---

### Post by varunendra on 2011-06-26
> **aerofly5 said:**
> ..I want to dual boot with Windows 7. I don't have any DVDs and my motherboard is too old to support booting off usb devices.....Please note that I have about 5 hard drives in this machine, so that may widen the possible solutions
No verified ideas other than using DVD or USB. But if you have Win7 DVD's iso and can devote one of your hard disks for an experiment (no valuable data should be on it!), then here's a stupid idea-

[LIST]
[*]Install VirtualBox or VMware on your current OS,
[*]create a virtual Win7 machine, with no hard disk in it.
[*]add your 'experimental' physical hard disk as virtual machine's hard disk. This step is quite trivial in VMware workstation, but may require some effort in Virtualbox. Here's a howto for VBox: [http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software](http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software) (you may also search the official site for stepwise help),
[*]boot your virtual machine with Win7 iso and install it.
[*]After completion, shut down virtual machine, detach hard disk, delete the virtual machine,
[*]reboot computer, invoke boot menu, choose to boot from the 'experimental' hard disk.
[*]Since Win7 is now installed on the hard disk, it 'should' at least try to boot,
[*]but since the hardware is now changed (real against virtual), I can't say what'll happen next! So better try this booting step with all other hard drives detached from mother board. :)
[/LIST]
As it sounds, it's definitely a crazy idea, so you may wish to look for other options, if any, before trying this.


**PS:** The idea of using another PC in the above post is better than trying Virtual machine I guess. As for any possibility of GRUB related troubles, it simply won't happen if GRUB (and ubuntu) reside on one hard disk, and Windows is on another one (the 'experimental' one). You'd just need to choose from BIOS boot menu everytime you want to switch between different OSes.

---

### Post by MartyBuntu on 2011-06-26
> **aerofly5 said:**
> My computer currently has Ubuntu 10.10 running on it, however I want to dual boot with Windows 7.

Are you sure that a computer so old that it doesn't have the ability to boot from USB will be able to handle Windows 7.

Boot-from-USB has been around for quite a long time. How old is this computer?

Hope you didn't pay too much for Windows 7.

---

### Post by varunendra on 2011-06-26
> **MartyBuntu said:**
> Are you sure that a computer so old that it doesn't have the ability to boot from USB will be able to handle Windows 7.
Good point!
But I'm typing this post from an HP dx2480 with Core2Duo E7400, 1GB DDR2, G31 chipset, .... and don't have the ability to boot from a USB flash drive. It has options to boot off USB HDD or USB CD drive, but not a flash drive (I've tried every setting in the past with no success). On the other hand, I have a couple of 'retired' PCs around (IBM, HCL, assembled....) which boot perfectly with the same live flash!

So incidently (and hopefully), age may not be a factor. But the amount of RAM IS a factor (at least 1GB for Win7).

---

### Post by mips on 2011-06-26
> **varunendra said:**
> Good point!
But I'm typing this post from an HP dx2480 with Core2Duo E7400, 1GB DDR2, G31 chipset, .... and don't have the ability to boot from a USB flash drive. It has options to boot off USB HDD or USB CD drive, but not a flash drive (I've tried every setting in the past with no success). On the other hand, I have a couple of 'retired' PCs around (IBM, HCL, assembled....) which boot perfectly with the same live flash!

So incidently (and hopefully), age may not be a factor. But the amount of RAM IS a factor (at least 1GB for Win7).

The USB HDD option should work and that PC is relatively new.

Try a different USB stick. My HP laptop will not boot from one specific flash stick for some odd reason although all my other PC's will boot of it. Other flash sticks work fine on the laptop though.

Also mayby check for a bios/firmware update on the HP site.

---

### Post by varunendra on 2011-06-26
> **mips said:**
> The USB HDD option should work and that PC is relatively new.

Try a different USB stick. My HP laptop will not boot from one specific flash stick for some odd reason although all my other PC's will boot of it. Other flash sticks work fine on the laptop though.

Also mayby check for a bios/firmware update on the HP site.
Yeah, I've also had a similar experience with a PC (it was some model from HCL) booting from one USB stick and not from another. So I tried on this one a PNY 1GB, Transcend 8GB, Kingston 4GB (two different types) .. not to avail.

I've also seen (very frequently indeed) USB sticks getting listed under Floppy or Hard disk lists in BIOS, perhaps due to their embedded emulation types. So I also tried every option other than native hard drives after plugging in those USB sticks (I desperately needed that, as I didn't want two PCs on my desk- one just for USB testing!), but same result.

As for BIOS update, I don't remember when I last checked it, but at that time, it was same version as I already had. So I concluded that perhaps the HP guys designed this BIOS in a hurry! :)

Hope someone finds this info useful.



**PS: **And yeah, USB HDD works just fine on it. In fact i ended up with this solution - making a FAT32 partition on my portable 320GB USB HDD - just for Live OS testing!

---

### Post by Sylslay on 2011-06-26
If You have CD drive use 

ploop boot manager and will be able to boot from USB

[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

