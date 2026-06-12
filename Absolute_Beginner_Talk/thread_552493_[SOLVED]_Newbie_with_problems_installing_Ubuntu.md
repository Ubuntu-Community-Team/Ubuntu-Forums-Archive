---
title: "[SOLVED] Newbie with problems installing Ubuntu"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by trueclearlight on 2007-09-16
Hi, I am totally new to Linux and am having trouble getting the Ubuntu 7.04 live -CD to run. When I can get it to work I want to get rid of XP and just have Ubuntu installed. I have looked in other posts and tried a few things, but still no luck (it doesn't help that I don't know that much about PCs, and even less about Linux).

The machine is an Intel P3 550MHz with 384MB RAM, 12GB HDD and NVIDIA GeForce4 MX420 graphics card. It is curently hooked up to a Iiyama (MF-851 5G) Vision Master 350 monitor. If it helps the BIOS version/date is given as American Megatrends Inc 62710 20/05/1999

So far today I have achieved this: 

-burn live-CD, start machine, choose option 1 from menu to run/install Ububtu, everything looks all OK and as if it is going to run , then left hanging with a blank screen when it looks like the OS is ready to start.

-choose option 2 from menu to start in graphics safe mode and end up with this  message:
BIOS 1999 fails cut-off (2000), acpi=force is required to enable ACPI 

Viewing details of the problem gives this information:
(EE) cannot read V_BIOS
(EE) Screen(s) found, but none have a useable configuration

Reading from earlier threads I tried to disable ACPI in the BIOS, but could only find options for CPI, not ACPI. Next I tried to set the card driver to vesa using the 'sudo dpkg-reconfigure xserver-xorg' command. This only changed the error message I was getting from '(EE) cannot read V_BIOS' to '(EE) VESA(O):cannot read V_BIOS' (which is the one I continue to get now). 

I have also tried to use the 'sudo lspci' command to try and get the video card BUS ID (as prompted) but was told the value was invalid when I entered it (although not quite sure exactly which information was required). This did reveal an Intel(R) 82810 Graphics Controller to be present, which I have seen is disabled when I run XP.

I hope I have provided enough information for someone to be able to help and that this post is not as confused as I am! Please assume I know nothing when supplying instructions in any replies. Many thanks for saving me from Windows (I hope).

---

### Post by mocoloco on 2007-09-16
It's possible you just have a bad disc.  Try the "check CD for defects" option and let that run.  Also I would say try another liveCD [(Knoppix]("http://www.knoppix.org/") is a good one) to see if another distribution will boot.

---

### Post by str8line on 2007-09-16
Considering that you want to jump away from M$ and go exclusive to Ubuntu, with your PC stats I would recommend using an alternative install CD instead of the Live CD.  This will allow you to do the install in text mode and avoid some of the problems you have had so far.

---

### Post by chrome307 on 2007-09-16
As you have problems with Feisty Fawn, why not try Xubuntu which has less hardware requirements to run/install.

**Minimum system requirements**

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

Ignore the fact this is talking about Feisty Fawn, but consider how your going to use your HDD 

[img]http://i8.tinypic.com/6gir7k1.jpg[/img]

You can do a 'manual install' from the Live CD and just set up your partitions as needed ........ don't let it do it automatically as it will just use up all the available free space.

eg

Partition 1 = your OS  (3GB?)
Partition 2 = your personal files (8GB?)
Linux Swap = virtual memory .... leave this a 1GB

---

### Post by jimrz on 2007-09-16
there is a BIOS cutoff date of 2000 for acpi. try a boot parameter of
```
acpi=force
```

this works for my old thinkpad 600x which still shows a date of 1999 , although the updated BIOS it is using meet the cutoff but somewhere in there i guess a date string did not get changed, with feisty. On that machine I also have to add
```
pci=noacpi
```
in order for my pcmia cards to function.

your mileage may vary

---

### Post by trueclearlight on 2007-09-17
-Mocoloco- I checked disk integrity and the disk is OK

-Str8line- Alternate CD may be best option if I can't get anything else to work. Where can I get one and how does it work? Will I have similar problems with the graphics display?

-chrome307- tried Xubuntu live CD, but had the same issues

-jimrz- adding acpi=force parameter did help (did not try pci=noacpi)

Still get left with blank screen if try boot normal mode, but get different message (After the 'Failed to start X server' error screen ) now when booting in safe graphics mode:

(WW) VESA: NO matching Device section for instance (BUS ID PCI:1:0:0)
(EE) VESA (0) cannot read V_BIOS
(EE) Screen(s) found, but none have a useable configuration

I am pretty sure this is to do with the graphics card and drivers, right? Not quite sure how to rectify it as I can't figure out which information I need to put where .I have read another thread suggesting a solution for similar problem is to edit video driver/screen values using sudo nano /etc/X11/xorg.conf command, but I don't think I'm doing it right. Is this a likely solution and worth trying to get right?

Thanks for all your suggestions, I'm sure I can get there in the end!

---

### Post by trueclearlight on 2007-09-19
Problem solved! the acpi=force parameter entered as boot option solved the BIOS problem and removing the GeForce card and just runing the onboard intel card solved the display problem (suggestion from a mate of mine who's running linux). Now I just need to try and get the right drivers for the graphics card once I've completed the install. Thanks for all the help :D

---

