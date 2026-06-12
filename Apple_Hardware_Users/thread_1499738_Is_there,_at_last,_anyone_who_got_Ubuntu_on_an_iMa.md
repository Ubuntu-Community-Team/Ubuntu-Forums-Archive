---
title: "Is there, at last, anyone who got Ubuntu on an iMac G5?"
date: 2010-06-02
forum: Apple Hardware Users
---

### Post by c-a-b on 2010-06-02
I have nothing but problems with installing Ubuntu in almost any version on my iMac G5 2 GHz with an ATI Radeon 9600. Newer Ubuntu versions like 8.x and 9.x everytime get stuck while the partitioning tool should be launched and live versions everytime get stuck while launching desktop. 

Ni idea what to try next. Is there anyone who managed an Ubuntu additional to MacOS X on an iMac? 

I also tried Ubuntu 10.04 lucid alternate but it remained too at the partitioning tool.

---

### Post by linuxopjemac on 2010-06-02
Forget my post, you have to use a 64-bits kernel.

---

### Post by Frobber on 2010-06-02
I have an 20", IMac G5, 1.8Ghz PPC, with nvidia geforce video. I am configured for tripple boot, Deb, Ubuntu, and macosx. Have had essentially no problems with Debian Lenny for PPC and a few problems with Ubuntu 10.4. Most of my problems are video and xorg.conf (the lack of when installed).

For Ubuntu 10.4 it takes a lot of tweaking. Create xorg.conf, Modify /etc/fstab, changing UID and GID to be compatable with OSX.

For install and live boot from cd I use the ppc64 options (live-powerpc64).

---

### Post by c-a-b on 2010-06-02
I also tried "install powerpc64" at start but there was also no way beyond the partitioning tool. :-( 

I liked Ubuntu 10.04 from the scratch so I wanted to install it next to my Leopard on my iMac G5. But sadly, it isn't that easy... 

On my MacBook Pro I managed getting Ubuntu 10.04 on a virtual machine. But I want some more than that...

---

### Post by Frobber on 2010-06-02
Okay, Prior to attempting installation, while still in the 'live' session open the System/Admin/Disk utility. Select the disk partition you want to use for ubuntu. Delete that partition. This will give you xGB 'free space'. Exit the disk utility, then install.
I typically, use the 'manual' option of the partitioning tool for the installation select the 'free space' partition and set it up manually. Another option is use the option to install the system in the largest continous 'free space'. Either one should work.

My reason for manual partitioning is to use ext3 format - its compatable with debian lenny; and I can exchange files with each side.

---

### Post by c-a-b on 2010-06-03
But I don't reach that point, whether in "Live" nor in "install" mode. And I don't want to delete all my other data and MacOS X?

---

### Post by c-a-b on 2010-06-03
Don't know how, don't know why... but an Ubuntu Live 6.~ CD did work and I got til the Live Desktop. Installing, however, failed while partitioning with an unusual view of my hard disk: 

[[img]http://www.abload.de/thumb/p6030019c5qa.jpg[/img]](http://www.abload.de/image.php?img=p6030019c5qa.jpg)

MacOS X says that around 80 GB are free, there are no additional partitions that I know. So what's this? Can anyone help me?

---

### Post by WolfRage on 2010-06-03
The older Ubuntu disc worked because Ubuntu stopped supporting the Power PC architecture after 6.10. So 6.10 and older versions of Ubuntu will work fine. If you want a modern free Linux OS capable of running on PPC architecture then Debian is the way to go; Fedora 12 is also the last version of Fedora that will support PPC. Sorry but in Linux support for PPC has really dropped off.

---

### Post by Frobber on 2010-06-03
Okay, I see what your problem is. Backup your data to an external place. I used DVDs. You need to go back to the MAC OSX install and partition your disk. Make one partition for the MAC OS, and one for Linux. 

I have my disk divided in 7 partitions 32GB each. I formated the first partition HFS+ (Mac extender non-journaled). The second partition Mac OS extended journaled. And the remaining five partitions HFS+ (mac extended non-journaled). Re-install OSX on the second partition. Re-install all my mac related software on the second partition. Made the third partition 'data' where all my files are located. 

Boot into the Ubuntu live cd. Go to the disk partitioner and delete the first 32GB partition. This will designate the 32 GB free space. Now install Ubuntu using continuous free space. I still have three partitions to play with for what ever.

---

### Post by Frobber on 2010-06-03
After my last post, I noted that I had neglected some items. Your posted picture shows you selected a 128MB piece of the drive. When Mac partitions a hard drive it puts 128MB buffers between the partitions. Linux disk partitioners show these and other small partitions (boot sector). DON'T delete these.

Another issue is you need to install MAC OS first; the reason, Linux puts a yaboot loader in the first partition. This yaboot allows you to select linux, macosx, or cdrom to boot. When the OSX install disk is booted it will overwrite this yaboot. Not too much fun to recover.

---

### Post by 828688 Ben on 2010-07-12
Here are the xorg.conf settings that work great for me:
 > Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"    
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
    DefaultDepth 24
SubSection "Display"
    Depth 24
    Modes "[SIZE=2]**_Enter Your Screen Resolution in between the parenthesis_**[/SIZE]"
EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection  

Try and see if this works for you.

Hope this helps,
Ben

---

