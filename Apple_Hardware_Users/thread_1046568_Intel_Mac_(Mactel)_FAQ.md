---
title: "Intel Mac (Mactel) FAQ"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by cyberdork33 on 2009-01-21
[I]**Welcome to the Apple Users Forum at ubuntuforums.org.** 
This forum is focused on providing community support on the installation and setup of Ubuntu running on Apple hardware.

[/I]This FAQ is targeted at Users with a Intel-based Macintosh computers (mactel) with Core and Core 2 CPUs or Xeon. If you have a PowerPC-based Mac (G3, G4, G5) Please see the [PowerPC FAQ]("http://ubuntuforums.org/showthread.php?t=427714"). Please be sure to always check this FAQ and the [Mactel-Support Community Support Documentation]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages") before asking a question in the forum, and when asking a question in the forum, post your [Mac's version string]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Determine%20your%20model%20and%20hardware%20revision").

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Can I run Ubuntu on my Mac?[/COLOR][/SIZE][/FONT]
YES! You will have to reduce the size of your OSX partition in order to make room for Ubuntu.

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]How do I install Ubuntu on my Mac?[/COLOR][/SIZE][/FONT]
*(keywords: installation, vm, virtual machine, vmware, parallels, virtualbox)*
 Several scenarios for installing Ubuntu on an Intel Mac have been covered in the [AppleIntelInstallation wiki page]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation"). If you are not ready to take the plunge and just what to try out Ubuntu, you can use a Virtual Machine running in OS X. [VirtualBox]("http://www.virtualbox.org/") is a free, open-source virtual machine that runs on a Mac.

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Can I install / boot Ubuntu from an external drive?[/COLOR][/SIZE][/FONT]
*(keywords: installation, usb, firewire, external drive)*
   The short answer is, "no" (Though [few]("http://ubuntuforums.org/showthread.php?t=869324") and far between have claimed, "yes"). 
If you are willing to try something new. You can try [booting via EFI]("http://ubuntuforums.org/showthread.php?t=995704").
You also may be interested in trying a [Boot CD]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/").
Reference: [Old External Booting Discussion]("http://ubuntuforums.org/showthread.php?t=510030")

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]What about Parallels / VMWare Fusion / VirtualBox / Virtual Machine X?[/COLOR][/SIZE][/FONT]
*(keywords: installation, vm, virtual machine, vmware, parallels, virtualbox)*
Installing in a virtual machine is not quite the same undertaking as "Installing on your Mac". A virtual machine creates virtual hardware, including a virtual hard disk (contained in an image file) that you install to. You can ask questions in the forum here, but please make sure that you indicate you are using a virtual machine. You should also check the support forums for your virtual machine for specific help as well as ubuntuforums.org's [Virtualization forum]("http://ubuntuforums.org/forumdisplay.php?f=308")
[Parallels Desktop Support Forum]("http://forum.parallels.com/forumdisplay.php?f=58")
[VMWare Fusion Support Forum]("http://communities.vmware.com/community/vmtn/desktop/fusion")
[Virtual Box on OS X Hosts Forum]("http://forums.virtualbox.org/viewforum.php?f=8&sid=eeaeeca77c621ffdb91fbd60e490703c")

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Should I use 32 bit or 64 bit?[/COLOR][/SIZE][/FONT]
*(keywords: 32bit, 64bit, x86, x86_64, x64, amd64)*
If you have a Mac with a Core CPU (not Core 2) then you can only use the 32 bit Ubuntu. If you have a Core 2 or Xeon, then which you pick is really up to you and what you plan to do. The 64 bit Users Forum has a great guide to the [Pros and Cons of using 64 bit]("http://ubuntuforums.org/showthread.php?t=765428"). NOTE that if you have 4GB or more of RAM, then you will likely need to choose the 64 bit version in order to utilize all the RAM.

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]What is rEFIt?[/COLOR][/SIZE][/FONT]
*(keywords: efi, menu, bootloader, partitioning)*
rEFIt is a nice-looking boot selector for your Mac. It will prompt you to choose a partition to boot upon starting up and will default to booting OSX after a short timeout period. It also has some nifty utilities that are helpful when dealing with multiple operating systems on your Mac. rEFIt _cannot_ partition your hard drive. rEFIt _is not_ a boot loader.
[The rEFIt Project Website]("http://refit.sourceforge.net/")

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Can rEFIt damage my Mac's firmware / void my warranty?[/COLOR][/SIZE][/FONT]
*(keywords: efi, menu, bootloader, partitioning, break, applecare)*
 rEFIt is not firmware. It is an efi executable. The Mac firmware (EFI) looks for efi executables in certain locations on a hard drive and will allow you to run them. It is much like having an app in OSX. You can easily remove rEFIt [following the directions on their website]("http://refit.sourceforge.net/doc/c1s3_remove.html"). Some Apple store employees have claimed that rEFIt can break your Mac. There has been no evidence that this is true. If you are concerned about voiding your warranty, or Apple not covering an issue because of rEFIt, uninstall it.

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]I installed, but Ubuntu won't boot / says "no bootable devices" / has a blinking cursor![/COLOR][/SIZE][/FONT]
*(keywords: bug, installer, mbr, gpt, partition tables, no operating system)*
  There is and has been for a long time, [a bug in the Ubuntu installer]("https://bugs.launchpad.net/mactel-support/+bug/222126") that leaves your system unbootable after installing Ubuntu. It is easily repairable.
[Syncing Partition Tables]("http://ubuntuforums.org/showthread.php?t=767677")
[Reinstalling GRUB]("http://ubuntuforums.org/showpost.php?p=3303463&postcount=11")
[Supporting Technical Data for Bug]("http://ubuntuforums.org/showthread.php?t=980938")

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]What is the Mactel-Support PPA Repository?[/COLOR][/SIZE][/FONT]
*(keywords: mac, intel, mactel, team, support, apple, software, fixes, driver, repo)*
  Several savy Ubuntu Mac users have fixed bugs, and added functionality to certain software in order to make Ubuntu run better on certain Macs and placed them in a [repository available to Ubuntu users]("https://wiki.ubuntu.com/MactelSupportTeam/PPA") until the fixes make it in to the main Ubuntu release.

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Can I boot Ubuntu directly from EFI?[/COLOR][/SIZE][/FONT]
*(keywords: efi, bootloader, grub2, grub-efi, elilo)*
  This would be the ideal way to boot Ubuntu Linux on your Mac, but it is still, as of yet, relatively unsupported. If you would like to try it out see below.
[GRUB-EFI Installation Information]("http://ubuntuforums.org/showthread.php?t=995704")

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Why does the battery monitor not show the right percentage? (and other strange power-related problems).[/COLOR][/SIZE][/FONT]
                  *(keywords: power, suspend, battery, charge, capacity)*
  Try [resetting the SMC]("http://support.apple.com/kb/HT1411").

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]How can I have Ubuntu on an encrypted partition?[/COLOR][/SIZE][/FONT]
*(keywords: encryption, partition, install)*
[HOW-TO: Dual-boot with Ubuntu encrypted]("http://ubuntuforums.org/showthread.php?p=4604645")

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Why is there are long delay booting up with only Ubuntu installed?[/COLOR][/SIZE][/FONT]
*(keywords: delay, efi, mbr, single-boot, ubuntu only, bless)*
  Because of how the Mac firmware works, it does not readily look for what Apple calls a "legacy OS" and searches for an EFI executable before resorting to starting the Linux bootloader. You can shorten this wait time by [blessing the Linux partition]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21").

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]How can I assign Right-Click to a keyboard key?[/COLOR][/SIZE][/FONT]
*(keywords: keyboard, mouse, mapping, xorg, shortcut)*
  There is a [forum post]("http://ubuntuforums.org/showpost.php?p=5801976") on remapping keys for this purpose. It may be useful to others remapping keys as well.

---

### Post by cyberdork33 on 2009-01-21
Old FAQ is [here]("http://ubuntuforums.org/showthread.php?t=493393"), but is quite outdated and may contain incorrect information. Please use only for informational purposes and as a last resort.

Other tips and info for reference...

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Why does the "alsamixer" tool only show PulseAudio?[/COLOR][/SIZE][/FONT]
*(keywords: sound, alsa, mixer, pulseaudio)*
  Ubuntu moved to using the pulseaudio sound server. You can still control the underlying alsa mixer by using this command to start alsamixer:
```
alsamixer -c 0
```

[FONT=Comic Sans MS][SIZE=3][COLOR=Blue] [/COLOR][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=3][COLOR=Blue]How do I get my sound to work the way I need?[/COLOR][/SIZE][/FONT]
*(keywords: sound, alsa, mixer, pulseaudio)*
 If you're saying "I've tried all the fixes in the wiki, and I still can't get my sound to work the way I need" then you might try installing some of the utilities mentioned [in this post]("http://ubuntuforums.org/showpost.php?p=7377913&postcount=5") in order to enable/disable things.[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]

Where can I find an application like X on OSX?[/COLOR][/SIZE][/FONT]
*(keywords: software, osx, switching, application, app)*
  Check out the "[Switching to Ubuntu From Mac OS X]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromMacOSX")" wiki page.

---

### Post by pxwpxw on 2009-01-23
Thats looking good,  and it is time the sticky was brought up to date. Maybe an appended links list with more descriptive titles than [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6606731&postcount=3") would be useful.
This post can be a place marker for such additions.

---

### Post by cyberdork33 on 2009-01-24
> **pxwpxw said:**
> Thats looking good,  and it is time the sticky was brought up to date. Maybe an appended links list with more descriptive titles than [[COLOR=Magenta]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6606731&postcount=3") would be useful.
This post can be a place marker for such additions.
I was going for something more like a traditional FAQ with questions and answers, which the old version had veered far from.

---

### Post by pxwpxw on 2009-01-24
> **cyberdork33 said:**
> I was going for something more like a traditional FAQ with questions and answers, which the old version had veered far from.

The FAQ format is good. I just think it is better if link names  convey their target's subject (or heading) to the reader at first glance, as most of yours do. Like the links in our signatures.

---

### Post by cyberdork33 on 2009-01-24
OK, I tried to make the links a bit more descriptive.

---

### Post by Gen2ly on 2009-02-26
Nice faq cyber.  Keep up the good work.

---

### Post by cyberdork33 on 2009-02-26
> **Dirk.R.Gently said:**
> Nice faq cyber.  Keep up the good work.
yes, the old one was getting a bit behind the times, especially with all the wiki documentation we have now. thanks!

---

### Post by buldozerceto on 2009-04-01
I don't get this:
Can I run Ubuntu on my Mac?
YES! You will have to reduce the size of your OSX partition in order to make room for Ubuntu.

Why I need to reduce the size of the OSX partition?

---

### Post by cyberdork33 on 2009-04-02
> **buldozerceto said:**
> I don't get this:
Can I run Ubuntu on my Mac?
YES! You will have to reduce the size of your OSX partition in order to make room for Ubuntu.

Why I need to reduce the size of the OSX partition?
Where else are you going to install it?

---

### Post by guja_nebeska on 2009-04-12
I hope this is appropriate thread to ask.

Is it possible to install Ubuntu on Macbook (I have 2,1 Macbook, I think, 2.1Core2Duo, Intel, black, 1G RAM, bought in summer 2007) without installing OS X?

As far as I figured out, EFI partition is something that must exist, but still don't get all things.

Thank You in advance for any kind of answer.

---

### Post by cyberdork33 on 2009-04-12
> **guja_nebeska said:**
> I hope this is appropriate thread to ask.

Is it possible to install Ubuntu on Macbook (I have 2,1 Macbook, I think, 2.1Core2Duo, Intel, black, 1G RAM, bought in summer 2007) without installing OS X?

As far as I figured out, EFI partition is something that must exist, but still don't get all things.

Thank You in advance for any kind of answer.
You do not have to have a GPT formatted disk. (i.e. don't have to have the EFI partition.)

The second topic in the FAQ deals with how you can install:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by guja_nebeska on 2009-04-12
I have managed to install only Ubuntu on macbook. Problem was that I was constantly trying to install Ubuntu on some partition scheme that wasn't good. Then I made new partition scheme by selecting msdos type, and then normally made partitions from installer, and everything works like a charm.

There's, dough, that problem with ~30 sec grey screen before GRUB shows up when booting system, but I can live with that. :-)

---

### Post by cyberdork33 on 2009-04-12
> **guja_nebeska said:**
>  There's, dough, that problem with ~30 sec grey screen before GRUB shows up when booting system, but I can live with that. :-)
There is also a question about that. You need to bless the Ubuntu partition.

---

### Post by guja_nebeska on 2009-04-12
How do you mean "bless it"? Bring a priest? :-D Kidding, of course. Any tutorial how to do that, maybe?

---

### Post by cyberdork33 on 2009-04-12
> **guja_nebeska said:**
> How do you mean "bless it"? Bring a priest? :-D Kidding, of course. Any tutorial how to do that, maybe?

See the first post of this FAQ.

---

### Post by davidgalbe on 2009-04-19
Hi, I have an Imac 24 intel core two duo already running both Mac Os and Windows 7 ultimate, with bootcamp. I want to to try ubuntu. Id like to have the three of them at start up. I got lost with the instruction and dont know what method i should use. Can i just make a 3rd partition and install ubuntu from the cd?....please help.

David Galbe

---

### Post by cyberdork33 on 2009-04-19
> **davidgalbe said:**
> Hi, I have an Imac 24 intel core two duo already running both Mac Os and Windows 7 ultimate, with bootcamp. I want to to try ubuntu. Id like to have the three of them at start up. I got lost with the instruction and dont know what method i should use. Can i just make a 3rd partition and install ubuntu from the cd?....please help.

David Galbe
please read the installation wiki:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I don't know how it will interact with Windows 7 since it is still a beta OS

---

### Post by noice742 on 2009-05-02
Hi

I have installed ubuntu 9.04 on my "top of the line" new iMac 24" , I dualboot it with Mac OSX. It runs fine. But i dont know how to make the sound to work. 
Can anyone help me, please?

Thanks,

Elin

:-k

---

### Post by cyberdork33 on 2009-05-02
> **noice742 said:**
> Hi

I have installed ubuntu 9.04 on my "top of the line" new iMac 24" , I dualboot it with Mac OSX. It runs fine. But i dont know how to make the sound to work. 
Can anyone help me, please?

Thanks,

Elin

:-k
you should start a thread for this.

---

### Post by noice742 on 2009-05-03
> **cyberdork33 said:**
> you should start a thread for this.

Okay. I have deleted it, couse i didnt get any help. :(
But i think i might test it again later on, could be good to know before i install ubuntu via bootcamp, how i am supposed to get everything working.

---

### Post by cRazYee on 2009-05-20
i'm using Intel Macbook Pro 2.4
install 64bit ubuntu via Virtual box, do i need to get the driver for my hardware?

---

### Post by cyberdork33 on 2009-05-20
> **cRazYee said:**
> i'm using Intel Macbook Pro 2.4
install 64bit ubuntu via Virtual box, do i need to get the driver for my hardware?
Installing in a VM doesn't require most of the stuff that you have to do when installing natively since the system sees different hardware in the VM than the 'real' hardware your machine has.

You should install the VirtualBox Guest Additions to get the VM hardware drivers.

---

### Post by techfanboy81 on 2009-06-10
Can I install Intel Mac (Mactel) on my iphone?  How?

---

### Post by cyberdork33 on 2009-06-10
> **techfanboy81 said:**
> Can I install Intel Mac (Mactel) on my iphone?  How?

Mactel is a term that means "Intel-based Mac", so I am not exactly sure what you are asking, but if you are trying to install Ubuntu on your iPhone, then no I do not think this is possible at this time.

---

### Post by Eemerica2s on 2009-06-16
So I installed ubuntu onto my Black MacBook and the last step told me I had to sync the disks, so I clicked on the DiskPartion tool in rEFIt and it told me it didn't need to sync, press any key to continue. But now when I try to go and boot up ubuntu, the penguin in the tux just sits there forever. How can I fix this?

---

### Post by cyberdork33 on 2009-06-16
> **Eemerica2s said:**
> So I installed ubuntu onto my Black MacBook and the last step told me I had to sync the disks, so I clicked on the DiskPartion tool in rEFIt and it told me it didn't need to sync, press any key to continue. But now when I try to go and boot up ubuntu, the penguin in the tux just sits there forever. How can I fix this?
shutdown, and startup a couple of times... (not a reboot, a shutdown and a startup)

---

### Post by quixote on 2009-07-16
One thing I'm not clear on with rEFIt:  when should it be installed?  

From OSX, before putting Ubuntu on the second partition?  Or go ahead and install the 2nd OS, and then install rEFIt from OSX?  From Ubuntu?

I don't use Macs much, so I tried to just install ubuntu and assumed grub would dual boot.  But it doesn't.  I gather I need something like rEFIt.

Assuming everything is set up right, what will my boot process look like?  Will rEFIt take over the function I'm used to grub doing?  I.e. letting me choose an OS.  Or would I have to do something extra to get at rEFIt, like hold down an ALT key, or something?

I can't find this spelled out anywhere.  It's probably so obvious to those who know, it doesn't usually need to be explained!

---

### Post by pxwpxw on 2009-07-16
Best to install refit first so it is there to use. But it can be installed any time provided you have OSX there to do it. You need it.

---

### Post by cyberdork33 on 2009-07-17
> **quixote said:**
> One thing I'm not clear on with rEFIt:  when should it be installed?  

From OSX, before putting Ubuntu on the second partition?  Or go ahead and install the 2nd OS, and then install rEFIt from OSX?  From Ubuntu?
I would install it before.

> **quixote said:**
> I don't use Macs much, so I tried to just install ubuntu and assumed grub would dual boot.  But it doesn't.  I gather I need something like rEFIt.You don't HAVE to, but it is a useful tool.

> **quixote said:**
> Assuming everything is set up right, what will my boot process look like?  Will rEFIt take over the function I'm used to grub doing?
No, rEFIt is an interface to the EFI subsystem of your Mac. It is, in itself, incapable of loading a Linux kernel. For that you still have to rely on GRUB (or LILO) 
> **quixote said:**
> I.e. letting me choose an OS.  Or would I have to do something extra to get at rEFIt, like hold down an ALT key, or something?
It will appear everytime you boot your machine. and allow you to choose between Linux and OSX, but you will also have to go through GRUB after that.
> **quixote said:**
> I can't find this spelled out anywhere.  It's probably so obvious to those who know, it doesn't usually need to be explained!

There is a lot of documentation in the wiki

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by quixote on 2009-07-17
Thanks for the answers, and for the very detailed one, cyberdork33!  Those are two very useful links at the end, especially the AppleIntelInstallation one.  I had about 30 sites bookmarked in the course of trying to figure this out, and neither of those ever came up.  Sometimes Google is *not* my friend.

---

### Post by Lucien.Malavard on 2009-11-11
Has anyone compiled an alternative LiveCD or installer CD that boots successfully and allows gparted to see the MacPro's harddrive? If so that would be a valuable contribution. None of Ubuntu's CD's from version 8.04 (x86 or x86_64) up to 9.10 work so far. It usually hangs after it gets to the point of booting up (maybe GRUB or GRUB2?) Choosing options like acpi=off and no apic does not help either. If there's a fix out there please help! The closest page I've seen so far is this [http://wiki.debian.org/DebianOnIntelMacPro](http://wiki.debian.org/DebianOnIntelMacPro), but I don't understand it at all. :confused:

---

### Post by jamesey on 2009-12-10
i think the guide needs to be updated for imacs and 9.10. something isnt quite right with my fresh install. I boot, use rEFIt to choose ubuntu and then i just see the word GRUB forever

---

### Post by sw3ex on 2009-12-14
I'm glad to know that I'm not the only one with the blinking cursor problem, would it be possible to post a good/simple tutorial on how to resolve this because I can't launch my windows partition either.
Ty

---

### Post by sw3ex on 2009-12-16
I have the impression that GRUB isn't installed because I can't find it using spotlight. Could this be possible?
To tell you exactly what I did to install Linux was booted onto the Live CD then installed ubuntu 9.10 on the bootcamp drive on which I already had Vista installed. But know I am unable to boot any of them. So any help would be welcome!

---

### Post by chillyperson23 on 2010-02-04
On my 27 inch iMac

I got it to boot up from the Live CD. At first the graphics didnt work right, but after installing the ATI Radeon Graphics driver, they worked fine. I had it running perfectly... except for one thing. No sound. The output monitors all say that there is sound, but there is no sound whatsoever. The speakers work fine in OS X though. Anyone else have this problem?

---

### Post by TehCodr on 2010-02-17
> **jamesey said:**
> i think the guide needs to be updated for imacs and 9.10. something isnt quite right with my fresh install. I boot, use rEFIt to choose ubuntu and then i just see the word GRUB forever

I'm barely sure if this is the answer, but did you create an approximately 600 megabyte partition formatted as ext32, and the rest of the desired space as swap, and then reinstall ubuntu with rEFIt or another partition manager/EFI?

---

### Post by Lokesh123 on 2010-02-26
> **jamesey said:**
> i think the guide needs to be updated for imacs and 9.10. something isnt quite right with my fresh install. I boot, use rEFIt to choose ubuntu and then i just see the word GRUB forever

It does not work for me either. I have an iMac with 10.4 on it, created 20 GB space, then run the installer and put Grub onto the root partition. rEFIt does not reports no syncing required. Thats it: no signs of Grub or Linux on startup. When I select the (uncoloured) Window image after pressing the alt tab the computer freezes. 

I have been searching on this for more than a week, but no clear hint found. Apple hardware is pretty standardised, should be straight forward to clarify  the issue...in theory.

Here is my setting: 

sda1:fat32, sda2:jhfs+, sda3 ext4, sda4: swap
boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640   440,811,559   440,401,920  af HFS
/dev/sda3         440,811,560   484,487,341    43,675,782  83 Linux
/dev/sda4         484,487,342   488,395,545     3,908,204  82 Linux swap / Solaris


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   440,811,559   440,401,920 HFS+
/dev/sda3     440,811,560   484,487,341    43,675,782 Linux or Data
/dev/sda4     484,487,342   488,395,545     3,908,204 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4646-150A                              vfat       EFI                           
/dev/sda2        731ab256-3f5a-3983-9b13-a309618c5b49   hfsplus    Macintosh HD                  
/dev/sda3        99dbb3ce-cf17-4df5-aa02-fa9d406e4a39   ext4                                     
/dev/sda4        20dc7859-25c0-419f-bb29-1ba0c286d8e0   swap  

It is so frustrating, for MacUsers Linux still does not seem to be an option. Maybe somebody knows the trick?

Cheers
Lokesh

---

### Post by las_vegas on 2010-03-01
For your configuration, boot into your Mac and mount the EFI partition with:

mkdir /efi
sudo mount -t msdos /dev/disk0s1 /efi

Once mounted, create a folder in EFI called "grub" and install the attached grup2 efi loader into that folder. Create a "grub.cfg" file in the same folder with the following info:

menuentry "Mac" {
    set root=(hd0.2)
    chainloader /usr/standalone/i386/boot.efi
}
menuentry "Ubuntu" {
    set root=(hd0,3)
    insmod ext2
    linux    /vmlinuz root=/dev/sda3
    initrd    /initrd.img
}

This should be enough to get you started. You will now have to bless the grub.efi with:

sudo bless --folder=/efi/EFI --file=/efi/EFI/grub/grub.efi --setBoot

I hope this helps...

LasVegas

Note: If the boot drive is any drive other than the internal drive0 (sda), the EFI partition has to be reformatted into HFS+. You should be able to get away with creating an EFI folder on the Mac partition and set it up the same. This way you wouldn't be messing with the EFI partition.

---

### Post by Lokesh123 on 2010-03-01
Hi Las Vegas

thank you for the advice, it worked!

Some additional information for those who are not yet there:
> **las_vegas said:**
> 
Once mounted, create a folder in EFI called "grub" and install the attached grup2 efi loader into that folder..

I unzipped the file first, which resulted in a grub22...efi file. I copied this into the target folder

> Create a "grub.cfg" file in the same folder with the following info:I did it by typing nano /efi/EFI/grub/grub.cfg in the terminal

> sudo bless --folder=/efi/EFI --file=/efi/EFI/grub/grub.efi --setBootI think the bless command is the most important step, file BTW should be grub22...efi instead.

Thanks again
Lokesh

---

### Post by las_vegas on 2010-03-01
> **Lokesh123 said:**
> 
I think the bless command is the most important step, file BTW should be grub22...efi instead.

I actually renamed the 'grup2202fat.efi' to 'grub.efi'. Either way works.

This also works very well for installing Ubuntu on a flash drive! The EFI partition has to be formatted as HFS+ though. Unfortunatly, I've so far been unsuccessful installing Kubuntu using the same technique. 

LasVegas

---

### Post by las_vegas on 2010-03-03
I was wrong about having to reformat the EFI partition to HFS+ on an external drive. It turns out, the Mac will in fact see the EFI partition in its original FAT32 format as long as the folders are arranged correctly. 

1) There must be an 'EFI' folder in the main directory.

2) Within that folder, there must be a folder containing the efi boot binary with one of a select set of approved names. I chose to use 'BOOT'; The most ubiquitous of the selections.

One of the problems with using the EFI, boot partition is that when a drive is formatted in GUID with Apple's Disk Utility, the EFI is always 200MiB and Apple, playing it safe, places 128MiB of free space between partitions. This isn't such a problem when using big hard drives, but when you want to install Linux on a flash drive, precious space is wasted.

One solution is to use the Kubuntu installer. The partition utility used in the installer allows partitioning a drive in the GUID scheme by defining the first partition (minimum 50MiB) as EFI. Unfortunately, while I really like the Kubuntu environment, the configuration and installation of drivers afterward is a pain, when possible at all.

The solution that I've come up with is relatively easy to accomplish and works using Mac OSX and the regular Ubuntu install CD. 

1) First, the drive must be partitioned in GUID previously using Apple's Disk Utility. Then boot into the Ubuntu CD Desktop.

2) Run "Terminal" from the Applications/Accessories menu and run 'sudo parted'

3) Enter 'print all' to determine which drive is your target drive and set that drive with the 'select <device>' command.

4) remove the Linux partition with  'rm 2' command.

5) resize the EFI partition with the command 'resize 1 0 50' (resize partition 1 to 50MiB)

6) If you previously changed the EFI partition by reformatting it, you may need to reformat it to FAT32 (mkfs 1 fat32) and set it back to an EFI partition (set 1 boot on).

7) Leave the remainder of the drive for partitioning and formatting in the Ubuntu installer. If you're using a flash drive, don't bother creating a swap partition. If it's a dedicated drive, use 1/2 or 1/4 of your physical memory for swap, but you shouldn't need more than 512MiB. Use 'ext4' for your Linux partition.

After installing Ubuntu, you need to boot back into OS X to install the EFI boot files. Use the Terminal to mount the EFI partition:
    mkdir /efi
    sudo mount msdos /dev/diskXs1 /efi     (where X is the target drive's number)

Create your 'EFI' folder and 'BOOT' within that folder. Place your grub.efi and grub.cfg within the BOOT folder.

Bless the EFI partition with "sudo bless folder=/efi/EFI/BOOT file=/efi/EFI/BOOT/grub.efi"

This boots without fail using the Option (alt) key boot sequence. Any future editing of the grub.cfg simply requires repeating the mount command above.

I hope this helps others!

LasVegas

---

### Post by untmdsprt on 2010-04-16
Here's another question that I haven't been able to find an answer for:

Why exactly would you want to use Ubuntu over the Mac OS? What software is out for Linux based OSs that isn't available for the Mac?

It's a no-brainer going from Windows to Ubuntu, but with Mac to Ubuntu, I'm like why?

Thanks for all those who can answer this question.

---

### Post by kagou on 2010-04-16
> **untmdsprt said:**
> Here's another question that I haven't been able to find an answer for:

Why exactly would you want to use Ubuntu over the Mac OS? What software is out for Linux based OSs that isn't available for the Mac?

It's a no-brainer going from Windows to Ubuntu, but with Mac to Ubuntu, I'm like why?

Thanks for all those who can answer this question.

May be to be free at last ?

---

### Post by untmdsprt on 2010-04-16
There has to be more than just "free at last." For my needs, I'm finding that Ubuntu is a good addition to, but not a replacement for the Mac.

I'm going to be taking a look at Ubuntu Studio when it finishes downloading. Too bad there isn't a PowerPC version. I have an old G4 tower full of recording equipment that it would be perfect for!

---

### Post by quixote on 2010-04-16
Ubuntu among linuxen for ease of use.  Linux generally for flexibility, adaptability, and the lack of middlemen getting between me and what I need.

Example 1: I blew up a special SD card full of irreplaceable photos. (No, it was not recoverable with normal tools.)  I had no idea what to do.  I did a bit of searching, found a program, it was already in synaptic, and one click installed it.  No "trial versions," no registrations, no credit cards, no crap. Then it took me an hour to recover the card because I was being s.u.p.e.r...c.a.r.e.f.u.l. 

Example 2: I decided I needed a vector-based drawing program.  Quick search yields Inkscape.  Download, install, done.

The fact that I can always get what I need when I need it is addictive for me.  When I have to work on relatives' Macs or PCs, I can't believe the BS they don't realize they don't have to put up with.

Last example: I want to move my music to my mp3 player.  I don't have to go through a bunch of steps to jailbreak anything. I don't have to go to itunes.  You may like itunes.  I can't stand it.  And that's the problem with Apple: one size fits all.  There's no choice.  And I get to pay through the nose for the privilege.  That doesn't work for me.  If their size happens to fit you, great.  If it fits so well you're happy to pay their prices, even better.

---

### Post by robertbub on 2010-04-21
> **untmdsprt said:**
> Why exactly would you want to use Ubuntu over the Mac OS?I have had to reinstall MacOSX 5 times in the last 5 years due to the fact that HFS is so utterly brain-dead (and MacOSX doesn't handle full disk conditions very well).  I have only once have ever had to reinstall Linux/Ubuntu over the last 15 years I've been using it.  Ext2/ext3/ext4 is much more reliable and Linux handles full hard drives much better.

My wife started depending upon iTunes and iPhoto and that was a mistake which I will eventually try to recover -- iTunes and iPhoto are completely incompatible with everything, AFAICT.  I'm going to work on transitioning her from Mac OSX to Ubuntu, but this is going to take some time

---

### Post by untmdsprt on 2010-04-21
> **robertbub said:**
> 

My wife started depending upon iTunes and iPhoto and that was a mistake which I will eventually try to recover -- iTunes and iPhoto are completely incompatible with everything, AFAICT.  I'm going to work on transitioning her from Mac OSX to Ubuntu, but this is going to take some time

I can relate to the iPhoto problem. I've had to reinstall my database from a backup and now all my RAW files are completely messed up. That part of it is going straight to Ubuntu, and have set up an external drive to capture all my RAW files straight from the camera. I'm tired of this crap!!

I'm going to work on seeing if iPhoto can burn those files to a CD.

---

### Post by patg7590 on 2010-05-06
> **untmdsprt said:**
> There has to be more than just "free at last." For my needs, I'm finding that Ubuntu is a good addition to, but not a replacement for the Mac.

I'm going to be taking a look at Ubuntu Studio when it finishes downloading. Too bad there isn't a PowerPC version. I have an old G4 tower full of recording equipment that it would be perfect for!

you could install xubuntu 9.10 for ppc and then maybe install the ubuntu-studio packages?

or is this a recipe for disaster?

---

### Post by untmdsprt on 2010-05-06
> **patg7590 said:**
> you could install xubuntu 9.10 for ppc and then maybe install the ubuntu-studio packages?

or is this a recipe for disaster?

There is a desktop version that would allow me to use a Live CD on the Mac without installing anything. This would be better since I wouldn't have to do anything.

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by quixote on 2010-05-06
It's a lot more than "free at last."  It's ease of installation, flexibility, accessible and knowledgeable community, hugely less expensive.  And that's just off the top of my head.  You're basically saying "Why are you people making your lives difficult when there's a much better and easier solution?"

For me, Apple stuff provides nothing I can't get faster, better and cheaper somewhere else.  So, on my side the question would be "Do you have so much money you want to throw it at Apple for nothing?"  

The first question is no more valid than the second one.  These things are a matter of personal preference.  You've asked, and we've told you what our preferences are based on.  There's not something wrong with us for preferring not-Macs, any more than there is with you for liking them.

(Just to be clear, I've used Macs for years.  Some of the software I need for my job runs only on Macs.  And I've installed and used hackintoshes for the hell of it.  I'm familiar with the OS and, for me, it's very limited compared to linux.)

---

### Post by Sunnz on 2010-05-29
> **quixote said:**
> 
Example 2: I decided I needed a vector-based drawing program.  Quick search yields Inkscape.  Download, install, done.

You can get Inkscape on OS X using the MacPorts package manager. Or just download it from the web.

> Last example: I want to move my music to my mp3 player.  I don't have to go through a bunch of steps to jailbreak anything. I don't have to go to itunes.  You may like itunes.  I can't stand it.  And that's the problem with Apple: one size fits all.  There's no choice.  And I get to pay through the nose for the privilege.  That doesn't work for me.  If their size happens to fit you, great.  If it fits so well you're happy to pay their prices, even better.

Surely you don't need to use iTunes on a Mac as long as your mp3 player doesn't require it. If your mp3 player do require iTunes to work then it is not going to work on Ubuntu anyway...

---

### Post by damagu on 2010-06-12
Maybe this is the wrong place to ask about this. If there is a better place for me to post this question, please let me know. 

I have a Macbook Pro 3,1. I have been running Ubuntu 9.10 successfully since it was in beta. Two days ago I ran the upgrade to Ubuntu 10.04 from the update manager. 

Since then, I have had some weird issues: 

* screen started strobing and I had to reboot
* graphics went into low resolution on log in and I had to reboot
* keyboard stopped working during the boot process so I couldn't log in at the log in screen. Rebooting fixed it.
* keyboard stopped working during boot process a second time. Choosing the USA keyboard instead of the USA Macintosh keyboard from the log in screen fixed the problem immediately. Since then I have left it on the USA layout. 
* trying to do anything with the keyboard layout (changing the layout, choosing different layout options, trying to use Xmodmap to switch Ctrl and Apple keys) causes this error to appear:
[FONT="Courier New"]
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10706000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd [/FONT]

But the worst thing so far is that after selecting Ubuntu from the Refit screen, the screen went blank and it wouldn't show grub or boot any further. Rebooting and powering off didn't help - I'd get a blank screen every time I chose Ubuntu from the refit screen. The first time this happened, I could still get into Mac OS instead and after leaving it over night, it worked fine. But yesterday it happened again and I couldn't even get into Mac OS. Every time I chose Ubuntu from refit I'd get a blank screen. Every time I chose Mac OS from refit I'd get the grey apple logo screen with the loading symbol and after 30secs or so the screen would darked and I'd get an error message saying I'd have to power off. Again leaving it off for a few hours seemed to sort it out. 

Now that it's working again (fingers crossed that it keeps working), my major problem is that the Ctrl and Command/Apple/Win keys need to be switched around. I like it the Mac way (eg. command+c = copy instead of ctrl+c). Using Ctrl for cut, copy, paste, undo, closing windows etc. is awkward. Previously, I've been able to do stuff with xmodmap to switch the functionality. But this time I just keep getting the error shown above and nothing changes. I had hoped that an option to switch these keys would become available in the keyboard layout options... but for some reason we are given a whole lot of far less useful options. 

So... has anyone experienced any of the problems I have? But more importantly for now, has anyone worked out to switch the keys yet?

---

### Post by damagu on 2010-06-22
Can anyone help with this keymapping issue?

---

### Post by shangjieok on 2010-07-27
Hello 
I was try to installed ubuntu 10.04 on the Macbook pro .But it was failed .I got following message:
/init: line 1: can't open /dev/sda: No medium found 

anyone can help?

---

### Post by quixote on 2010-07-28
/dev/sda not found means it's not finding your main hard drive for some reason.  That's a separate issue from this Mactel FAQ.  Repeat your question in a new thread, possibly in the Installation or General Help forums.  Include information on how many hard drives you have, and which operating systems are (supposed to be) on them.

---

### Post by seeker83 on 2010-08-05
This is a good FAQ.. Thanks for this..

---

### Post by LinuxMan92 on 2010-08-31
Maybe edit the 32/64 section to reflect the 2010 core processor lines? Just for those who dont know that a core i5 or i7 IS indeed 64bit capable.

---

### Post by TGIK on 2010-09-06
Hello yall,

    I just wanted to share my experiences of setting up a tripleboot on my MacBook Pro 1.1 ---

      One thing I found out along the way was that these early models of MacBook Pro's seemed more 'open' and flexible compared to some of my peers newer models I used. First off I was/am using Tiger because I use my Mac for making music [ [http://hypem.com/#/search/tgik/1/](http://hypem.com/#/search/tgik/1/)]  and have a setup that 'just works.' I always have trouble transferring everything over to a new OSX when it comes to Pro Tools RTAS and the like etc.... So immediately the option of using bootcamp to partition my drive was not an option (in August 2006 I didn't want to get the beta version) ----- but obviously after gleaning the internet, and a little common sense I realized that the main functioning of bootcamp [Live partition resizing, hybrid GPT/MBR etc.] was still written in the code just not through the GUI of Disk Utility -- only through terminal. I wanted a windows partition to run specific software, and also just to broaden the scope in general of the software I could use. I was also playing with a lot of live Linux OS's and found linux to be the ideal computer solution for most computer uses while its open belief was also emotionally appealing--- I wanted a permanent Linux solution. 

     At this time I also realized that I needed to upgrade my very small, original w/ computer 80GB hard drive--- I got a 320GB hard drive. So despite the fact that I could of made my partitions in terminal I now was going to have a clean drive to make partitions in. I took my computer to the best spot (though changing a hard drive is not hard) in San Francisco  [http://www.unionsquarecomputerrepair.com/](http://www.unionsquarecomputerrepair.com/) --  I told them to just put in the hard drive I didn't need an OS or a Restore since I had many clones of my startup disk on externals thanks to the wonderful CCC- [http://www.bombich.com/](http://www.bombich.com/)  - They said they had to put an OS on it but they would leave a large unpartitioned space at the end of the disk.
   
    When I got my MBP back I was happy and surprised to find that they had installed OSX 10.5.8--- which on my internal was no use to me but I could clone that and use it as a diagnostic OS through Firewire. I made the clone and then repartitioned my drive. At that time I got cold feet about a triple boot and just made 2 partitions -- A JHFS+ and a Fat32. Windows won out at the time. I chose to use Refit as a boot menu because of the way it looks and ease of use [http://refit.sourceforge.net/](http://refit.sourceforge.net/) -- so I cloned back my OSX to new JHFS+partition --- installed windows  by choosing disc at Refit menu  installed on FAT32 Partition (which was reformatted to NTFS) etc... Installation finished------- Used the Refit menu to make sure partition tables were in sync--- Booted into Windows.  This is where I lucked out because I have had trouble trying to install bootcomp drivers manually--- my friend had his OSX 10.5.8 DVD --- Popped it in, drivers installed-  Apps installed that I needed (a DAW and some WAVES plug-ins) and then made it a closed machine not using it on the internet. 

    So cool, I had my OSX and Windows. Now I wanted to install Linux on an external HD--which many have had trouble with. Two main issues are obviously which distribution and also what type of hard drive (USB powered? Flash? etc)  ---
I followed the directions for a USB install of Ubuntu, the main catches being making sure to install GRUB onto the drive not your internal MBR--- I was able to install Ubuntu on various drives both USB and AC powered and Flash drives------- they would appear on my refit boot and could load into them. On many other macbooks and macbook pros I would get a message saying that the firmware doesn't support booting 'Legacy (MBR) OS's' externally from USB -- Cool, I guess MBP 1.1 was more 'open.'  The problem with Ubuntu was that it was so slow after choosing at the GRUB Menu to boot----- Okay, success with linux on EXT USB --- but is there a faster solution ????

   Indeed there was in Open SUSE [http://www.opensuse.org/en/](http://www.opensuse.org/en/)-- I was able to make a boot-able OpenSuse disk very much in the same way as one would do with ubuntu (making sure you click advanced settings when it comes to bootloader installation) and it would boot incredibly fast. I realized with open suse that the hard drive must be self powered because during the boot process power is lost to the USB (so no portable flash drive solution either) --- in general self powered drives give me more piece of mind when running OS's off of them---  But being tethered is being stuck so that limitation was annoying---
 
   Then I found out about the ubuntu based jolicloud[ http://www.jolicloud.com/]("http://www.jolicloud.com/") -- this installed on my flashkey and booted super fast. That is the best distro for a flash drive --- but it isn't designed to be a full blown OS-- and again it is just resting on the USB connection----

Months later......

    I needed Ubuntu on my internal--- I was willing to lose windows if that's what it took. I decided that I could try to add another partition by making my mac partition smaller. This would max me out at the total 4 partitions one can have with a GPT MBR hybrid (1. EFI 2. OSX 3. for linux 4. Windows) ---- Did I need terminal? no? Because those great guys at [http://www.unionsquarecomputerrepair.com/](http://www.unionsquarecomputerrepair.com/) gave an OSX 10.5.8 I had a drive I could boot that up with and non-destructively re-size my OSX partition through the GUI disk utility. Resized it, made another partition JHFS+-----

     I used GEdit in Jolicloud to edit the boot.ini file for my Windows XP , changing the partition number now to 4 instead of 3. Booted into windows everything worked. I will admit that my computer did not like this transition phase giving me a flash of the dreaded '? mark folder' before the Refit menu appeared. I now was going to install ubuntu on that new partition-- following the triple boot guide[ https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") --- the most important point again being to manually choose the partition and not to create a  swap partition. Installed---- had to sync my partition tables and everything worked. I then made a 2GB swap file in lieu of a swap drive and finally!!!!!!

   I like that the process was drawn out over a long time --- the ability to go from double to triple w no loss is awesome and thanks to these forums and the internet in general. I still use my SUSE distro but not as much--- having all three major flavors is the best way you can have your computer --- Maybe a Mac Pro w lots of internal HD's would be a fun multi lingual project for next time......

---

### Post by srs5694 on 2010-09-06
> **TGIK said:**
> This would max me out at the total 4 partitions one can have with a GPT MBR hybrid (1. EFI 2. OSX 3. for linux 4. Windows)

There is no such limit -- at least, not in quite the way you seem to believe. A hybrid MBR configuration takes up to *three* (not four) GPT partitions and places them in the GPT's protective MBR. (Your partition #1, "EFI", is actually not a GPT partition -- it's a tiny little type-0xEE protective partition that does not correspond to any GPT partition, but flags the MBR as being a protective MBR for a GPT disk -- or in this case a hybrid MBR/GPT.) The intent and effect is to make those three partitions available to Windows, which gives priority to MBR data when it encounters a hybrid MBR. Both Linux and OS X give priority to GPT data when they encounter a hybrid MBR. With the right tools, such as recent versions of gptsync or [GPT fdisk,](http://www.rodsbooks.com/gdisk/) it's possible to specify which partitions go in the hybrid MBR. You could have a dozen GPT partitions and flag just one or two to be duplicated in the hybrid MBR.

One complication is that some boot loaders also favor MBR data, at least under some circumstances. This may make it difficult or impossible to boot an OS that's not represented in the hybrid MBR. Unfortunately, I'm not an expert on boot loaders for Mac hardware, so I can't give much advice on this score for Mac users. I do know it's possible to dual-boot Linux and OS X on a Mac using a conventional protective (non-hybrid) MBR, but you may need to jump through some extra hoops to get this working.

---

### Post by bpha on 2010-09-10
Hi,

I've been trying to install Ubuntu 10.04 on my MacBook Pro (5,3) and managed to follow the Mactel general directions all the way up to the point where I'm supposed to start the partitioning/install. In the directions it says to click on the advanced settings and make sure to install the boot loader/GRUB on sda3 (my setup is the usual, EFI on sda1 and OS X on sda2), but the pull-down list I get has no sda3, just the following:

sda
sda-1
sda1
sda2 OS X
sda-1 (don't know why it's there for a second time, something to do with swap?)

So, I didn't proceed with the install. Did try to create an sda3 partition on my own. Got sda3 (ext4) and sda4 (swap) created ok but even this way I couldn't get past the GRUB install location, as it doesn't let me install it on sda3.

In the beginning I used the OS X (10.6.4) disk utility to create an msdos partition, then deleted it after switching on to ubuntu live CD, but still can't get the gparted to create an sda3 partition to use for the GRUB. 

Any advice anyone?

---

### Post by TGIK on 2010-09-25
I might be able to help you-- I have a triple boot on my macbook pro --- let me know if you are still having trouble--



Cheers 

Derek 



TGIK 

[http://hypem.com/#/search/tgik/1/](http://hypem.com/#/search/tgik/1/)

---

### Post by Old Codger on 2010-10-25
The more I use Ubuntu, the more I like and prefer it to my Mac OS 10.6.4. I'm recently upgraded to Ubuntu 10.10 on my black MacBook and the install was quick and nearly flawless, but I still haven't figured out how to get iSight to work, but everything lese is fine.

Here's the problem: I decided to also install Ubuntu 10.10 on my relatively new iMac 10,1, but was unable to partition the HD using either Disk Utility or Boot Camp. Instead, I kept receiving an error message saying that I couldn't partition the drive because it couldn't verify the disk. :confused:

Ok, so I ran verify disk and disk repair and I STILL can't partition the disk.

Meanwhile, the rEFIt install was no problem and I could boot the Ubuntu 10.10 install CD, which I had prepared earlier. Since I couldn't install the distro, I thought I'd try seeing how the demo looked and worked on my iMac. At this point, it appeared that it wouldn't recognize either my wireless keyboard or wireless "magic Mouse." :rolleyes

Has anyone had a similar experience? Can anyone recommend a fix on partitioning and the possible keyboard/mouse problem?

Many thanks in advance,
f

---

### Post by Old Codger on 2010-10-26
[SOLVED] 

OK, I solved the partition problem on the 21" iMac 10,1, but needed to repair the disk by booting the install disk and using disk utility from there.

I then repartitioned the drive and installed Ubuntu 10.04, which worked like a charm. The wireless/bluetooth keyboard and mouse also worked...until I tried to install 10.10. So, I've just reinstalled 10.04 and it now works fine. I still need to resolve iSight, etc., but now I've got Ubuntu on both the iMac and MacBook (running 10.10).

---

### Post by swejap on 2010-11-01
> [FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Should I use 32 bit or 64 bit?[/COLOR][/SIZE][/FONT]
*(keywords: 32bit, 64bit, x86, x86_64, x64, amd64)*
If you have a Mac with a Core CPU (not Core 2) then you can only use the  32 bit Ubuntu. If you have a Core 2 or Xeon, then which you pick is  really up to you and what you plan to do. The 64 bit Users Forum has a  great guide to the [Pros and Cons of using 64 bit]("http://ubuntuforums.org/showthread.php?t=765428"). ** NOTE that if you have 4GB or more of RAM, then you will likely need to  choose the 64 bit version in order to utilize all the RAM.**Wish I had read this before installing 32-bit version on my macbook 5,1. The official Ubuntu homepage recommended 32-bit version and most Ubuntu users agree it is more stable.

So does this statement means I can't fully utilize all the RAM? Is there some way to upgrade to 64-bit? :P

---

### Post by CoreyB. on 2010-11-01
> **swejap said:**
> Wish I had read this before installing 32-bit version on my macbook 5,1. The official Ubuntu homepage recommended 32-bit version and most Ubuntu users agree it is more stable.

So does this statement means I can't fully utilize all the RAM? Is there some way to upgrade to 64-bit? :P

32-bit can use no more than ~4GB of RAM.  If you have more than that, 32-bit won't be able to use it.  There is no way to "upgrade" to 64-bit, you would have to re-install the 64-bit version.

---

### Post by swejap on 2010-11-01
> **CoreyB. said:**
> 32-bit can use no more than ~4GB of RAM.  If you have more than that, 32-bit won't be able to use it.  There is no way to "upgrade" to 64-bit, you would have to re-install the 64-bit version.

Then I'm fine running 32-bit because I can have no more than 4GB thats currently installed. Thanks for the reply!

---

### Post by srs5694 on 2010-11-01
> **swejap said:**
> Wish I had read this before installing 32-bit version on my macbook 5,1. The official Ubuntu homepage recommended 32-bit version and most Ubuntu users agree it is more stable.

I don't think I agree with the last part of this statement. The 32- vs. 64-bit issue has come up repeatedly in the few months I've been reading this forum, and in those threads that I've read, I've seen few or no posts suggesting that the 32-bit version is more stable than the 64-bit version. The main complaint against the 32-bit version is that a few bits of software, such as Flash, are more mature on the 32-bit platform. Most people seem to think that the speed improvements and better support for lots of RAM make the 64-bit version preferable, particularly on systems with lots of RAM.

My suspicion is that your impression that the 32-bit version is more stable comes from old posts or Web pages. When major distributions first began supporting the AMD64 platform, some of them did indeed have stability problems. I wasn't using Ubuntu at that time, but I seem to recall that SUSE had pretty dreadful AMD64 support back then. (Today it's fine, though.)

Many posts in this forum have lamented the official description of the 32-bit version as "recommended" vs. no such tag on the 64-bit version. This is certainly a case where the community as a whole disagrees with the official Ubuntu position on the issue.

---

### Post by kwiksand on 2010-11-02
Agreed, apart from some flash issues over about 2 years ago, I've seen absolutely no reason NOT to run 64bit install in years and years!

---

### Post by swejap on 2010-11-02
Thanks for the replies, makes things less confusing to hear it from you. Will run 64-bit version on my stationary computer from now on :)

Edit: After a few days with 64-bit version I noticed it runs more unstable than 32-bit. Maybe just for me tho? ;)

---

### Post by Fre3energy on 2010-12-09
Hello. I've successfully installed Ubuntu on my mac with Bootcamp as well. I was wondering which wireless driver was the right one to use, as the one recommended to me isn't installing properly. I have a macbook pro of the most recent update.

Thanks,
Robert

EDIT: I solved the problem by installing through Synaptic Package Manager. Thanks guys!

---

### Post by gaboguy7 on 2010-12-27
Hi, i'm trying to install Ubuntu 10.10 off a CD, to my macbook pro 6,2 with intel i5 processor, and when I go to install it wants me to connect to the internet. So i went to connect to the internet and typed in all the information I knew into the connection settings (ssid, mode, security and passphrase, mac address) but it doesn't connect. what do I do?

---

### Post by Tinka on 2011-01-07
> **gaboguy7 said:**
> Hi, i'm trying to install Ubuntu 10.10 off a CD, to my macbook pro 6,2 with intel i5 processor, and when I go to install it wants me to connect to the internet. So i went to connect to the internet and typed in all the information I knew into the connection settings (ssid, mode, security and passphrase, mac address) but it doesn't connect. what do I do?
I would definitely try with a Ethernet connection. There might be issues with your wireless card!

---

### Post by bilallucky on 2011-01-25
yap the old one was getting a bit behind the time especially with all the wiki documentation we have now.

---

### Post by teklife on 2011-02-17
> **gaboguy7 said:**
> Hi, i'm trying to install Ubuntu 10.10 off a CD, to my macbook pro 6,2 with intel i5 processor, and when I go to install it wants me to connect to the internet. So i went to connect to the internet and typed in all the information I knew into the connection settings (ssid, mode, security and passphrase, mac address) but it doesn't connect. what do I do?

go with pinguy os [http://pinguyos.com/](http://pinguyos.com/) which is a very slick ubuntu remix, and use this method here [http://sslove.posterous.com/how-to-triple-boot-your-mac-with-windows-and](http://sslove.posterous.com/how-to-triple-boot-your-mac-with-windows-and)

i've installed pinguy to several macintels and never had any problems at all. wireless works out of the box, plus many other great tweaks to ubuntu.

---

### Post by lazylew on 2011-04-09
> **untmdsprt said:**
> ...Why exactly would you want to use Ubuntu over the Mac OS? What software is out for Linux based OSs that isn't available for the Mac?...It's a no-brainer going from Windows to Ubuntu, but with Mac to Ubuntu, I'm like why?..and a variant to this question: 

my refurbished computer is very old - noisy and at least one of the 3 internal drives is dying slowly of old age. 
Also the learning curve of Linux is not too steep, but nevertheless never ending once you start fiddling around with settings a bit. 
This caused me to spend more time on computers than first intended - a nice new hobby, but too much time consuming.

Should I spend money on eg a mini-mac (dual booting with Linux for some programs) for stability and ease of use, or simply buy a more modern (less noise) pc?

---

### Post by lonflavio on 2011-05-14
Hi,

I'm having an issue with installing the graphics card, I cant get the first step on to work
[https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)

sudo apt-get install btusb-dkms applesmc-dkms hid-apple-dkms bcm5974-dkms xf86-input-multitouch snd-hda-dkms mbp-nvidia-bl-dkms -y

i get the following error

> flavio@flavio-MacBookAir:~$ sudo apt-get install btusb-dkms applesmc-dkms hid-apple-dkms bcm5974-dkms xf86-input-multitouch snd-hda-dkms mbp-nvidia-bl-dkms -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package btusb-dkms
E: Unable to locate package applesmc-dkms
E: Unable to locate package snd-hda-dkms
E: Unable to locate package mbp-nvidia-bl-dkms


I am running Ubuntu Ubuntu 11.04 64bit on a MacBook Air late 2010 11" (new model)

any suggestions?

---

### Post by guillermo112 on 2011-05-16
Are Mac good to play videogames?

---

### Post by handy on 2011-06-11
> **guillermo112 said:**
> Are Mac good to play videogames?

Yes, but there are many more games available for Windows, & for the price of a medium quality graphics card you can buy a PS3 or XBox, both of which have heaps of games that are dead easy to install & play, & can be obtained at very low prices if you are prepared to play games that are a year or so old, which is what I do on a PS3. You can also use the PS3 network for free if you like to play online games.

---

### Post by simonrodan on 2011-06-19
> **lonflavio said:**
> Hi,

I'm having an issue with installing the graphics card, I cant get the first step on to work
[https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)

sudo apt-get install btusb-dkms applesmc-dkms hid-apple-dkms bcm5974-dkms xf86-input-multitouch snd-hda-dkms mbp-nvidia-bl-dkms -y

i get the following error



I am running Ubuntu Ubuntu 11.04 64bit on a MacBook Air late 2010 11" (new model)

any suggestions?


I'm having the same problem. 

Following suggestions at: [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat/](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat/)

> 
sudo add-apt-repository ppa:mactel-support/ppa
sudo apt-get update
sudo apt-get install btusb-dkms applesmc-dkms hid-apple-dkms bcm5974-dkms xf86-input-multitouch snd-hda-dkms mbp-nvidia-bl-dkms -y

These packages are not found: 
btusb-dkms
hid-apple-dkms
bcm5974-dkms 
xf86-input-multitouch 
snd-hda-dkms
 
Any suggestions much appreciated.

---

### Post by CoreyB. on 2011-06-19
> **simonrodan said:**
> I'm having the same problem. 

Following suggestions at: [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat/](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat/)


These packages are not found: 
btusb-dkms
hid-apple-dkms
bcm5974-dkms 
xf86-input-multitouch 
snd-hda-dkms
 
Any suggestions much appreciated.

If you are running Natty (11.04), those packages are not in the Mactel ppa for that version.

[https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty]("https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty")

If you are actually running a MacBook Air 3,2 and Ubuntu 11.04, [this]("https://help.ubuntu.com/community/MacBookAir3-2/Narwhal") page on the community wiki may be more appropriate.

---

### Post by brodeur235 on 2011-06-26
Having the exact same problem as the above post. Anyone figure this out?

---

### Post by CoreyB. on 2011-06-27
> **brodeur235 said:**
> Having the exact same problem as the above post. Anyone figure this out?

If you mean you are having the same problem as simonrodan, the problem is that you are trying to install packages from the Mactel PPA that don't exist in Natty.  The page simonrodan was looking at was for Maverick (10.10), but he/she is actually running Natty (11.04), and the contents of the page don't really apply.

---

### Post by ATaghavi on 2011-06-30
Hey guys, I've got a 15" i7 Macbook 8,2. I've been trying the 32 bit and 64 bit Live CD versions but cannot seem to get them to run. The problem i get is "(initramfs) Unable to find a medium containing a live file system". Does anyone know what I can do to fix this? Help would be GREATLY appreciated as I'm tired of OS X and it's oppressive ways >:(

---

### Post by mambeu on 2011-07-02
> **ATaghavi said:**
> Hey guys, I've got a 15" i7 Macbook 8,2. I've been trying the 32 bit and 64 bit Live CD versions but cannot seem to get them to run. The problem i get is "(initramfs) Unable to find a medium containing a live file system". Does anyone know what I can do to fix this? Help would be GREATLY appreciated as I'm tired of OS X and it's oppressive ways >:(
I have a MacBook Pro 8,1 and the same problem.  32 bit 10.04, 32 bit 11.04, and 64 bit 11.04 are all unsuccessful, from both CDs/DVDs and USB sticks.  If I plug in an external hard drive, I can at least run the live CD ('try Ubuntu without installing'), but I can't install it.

Clearly there are people running Ubuntu on the same computer, so it's possible.  But what's the trick?

---

### Post by mambeu on 2011-07-03
I got Ubuntu installed on my new MacBook Pro (8,1)!

I also have a MacBook Pro 3,1 that is dual-booted with Ubuntu 10.04.  In Ubuntu, I downloaded the 11.10 Daily Build (64-bit Mac alternate install .iso) and followed the directions [here]("http://www.ubuntu.com/download/ubuntu/download") to create an install DVD and also a USB stick.  

I installed rEFIt on my new MacBook Pro, and shrunk the size of my Mac OS X partition from 1 TB to 800 GB, leaving 200 GB of free space.

I then plugged in the USB stick, inserted the DVD, and restarted the computer while holding the 'c' key to boot from the DVD.  I followed the install directions, choosing to install Ubuntu in the largest contiguous free space.

Wireless doesn't work, and the touchpad seems pretty glitchy, but I've removed the install media and confirmed that I can boot into Ubuntu without them.

It's taken me eight days of reading these forums and trying various methods, but I've finally got it installed.  Now to try to get things working properly...

---

### Post by ATaghavi on 2011-07-05
> **mambeu said:**
> I got Ubuntu installed on my new MacBook Pro (8,1)!

I also have a MacBook Pro 3,1 that is dual-booted with Ubuntu 10.04.  In Ubuntu, I downloaded the 11.10 Daily Build (64-bit Mac alternate install .iso) and followed the directions [here]("http://www.ubuntu.com/download/ubuntu/download") to create an install DVD and also a USB stick.  

I installed rEFIt on my new MacBook Pro, and shrunk the size of my Mac OS X partition from 1 TB to 800 GB, leaving 200 GB of free space.

I then plugged in the USB stick, inserted the DVD, and restarted the computer while holding the 'c' key to boot from the DVD.  I followed the install directions, choosing to install Ubuntu in the largest contiguous free space.

Wireless doesn't work, and the touchpad seems pretty glitchy, but I've removed the install media and confirmed that I can boot into Ubuntu without them.

It's taken me eight days of reading these forums and trying various methods, but I've finally got it installed.  Now to try to get things working properly...


Is it necessary to use the USB stick AND the DVD at the same time? Also, how did you get into Ubuntu on your MBPro to make the USB and DVD? Any help is GREATLY appreciated man. :D

---

### Post by mambeu on 2011-07-05
> **ATaghavi said:**
> Is it necessary to use the USB stick AND the DVD at the same time? Also, how did you get into Ubuntu on your MBPro to make the USB and DVD? Any help is GREATLY appreciated man. :D
I don't know if it's necessary to use both the USB stick and the DVD to install Ubuntu.  The impression that I got from reading the forums here was that the installer would use the files on the USB, but I don't really have any idea.

I have two MacBook Pros.  One is model 3,1 (late 2007) and is dual-booted with both Mac OS X and Ubuntu (10.04 LTS).  The other is the new 8,1 (early 2011).  I created the DVD and the install USB on the older MBP, in Ubuntu.  I thought maybe I'd have an easier time if the installation media were created in Ubuntu, but now that I think about it I'm not sure why it should make a difference.

I'm still new to Ubuntu, so don't take this as anything other than a wild guess, but the 11.10 daily build I installed (the alternate install .iso with the text installer) uses the 3.0.something kernel when the other releases I tried used 2.6.something.

I hope this helps you.  I'm still very much figuring things out myself.

---

### Post by amo3 on 2011-07-08
> **mambeu said:**
> I don't know if it's necessary to use both the USB stick and the DVD to install Ubuntu.  The impression that I got from reading the forums here was that the installer would use the files on the USB, but I don't really have any idea.

I have two MacBook Pros.  One is model 3,1 (late 2007) and is dual-booted with both Mac OS X and Ubuntu (10.04 LTS).  The other is the new 8,1 (early 2011).  I created the DVD and the install USB on the older MBP, in Ubuntu.  I thought maybe I'd have an easier time if the installation media were created in Ubuntu, but now that I think about it I'm not sure why it should make a difference.

I'm still new to Ubuntu, so don't take this as anything other than a wild guess, but the 11.10 daily build I installed (the alternate install .iso with the text installer) uses the 3.0.something kernel when the other releases I tried used 2.6.something.

I hope this helps you.  I'm still very much figuring things out myself.

I'm having the same issue, have been trying to get Ubuntu on my machine for days.  Currently downloading oneiric-alternate-amd64+mac (11.10) daily build to see if I can get the same results as you.

---

### Post by amo3 on 2011-07-08
> **amo3 said:**
> I'm having the same issue, have been trying to get Ubuntu on my machine for days.  Currently downloading oneiric-alternate-amd64+mac (11.10) daily build to see if I can get the same results as you.

Installation from CD failed for me with 11.10 alternate . Same issue, unable to detect any usable CD.

---

### Post by mambeu on 2011-07-09
> **amo3 said:**
> Installation from CD failed for me with 11.10 alternate . Same issue, unable to detect any usable CD.
Did you use a USB stick as well as the CD?  Maybe the USB is necessary after all.

---

### Post by amo3 on 2011-07-09
> **mambeu said:**
> Did you use a USB stick as well as the CD?  Maybe the USB is necessary after all.

USB and CD worked! Thank you very much! With the live CD it was automatic.. With the alternate install I needed to manually mount the USB to /cdrom with "mount -t iso9660 /dev/sdb /cdrom"

---

### Post by trungvkvk on 2011-07-14
I don't get this:
Can I run Ubuntu on my asus?

---

### Post by BDNiner on 2011-07-23
I just got a Mac mini and want to get all my ducks in a row before I install Ubuntu. Thank you guy for all the information.

---

### Post by jtaylor7192 on 2011-08-30
Can I install Ubuntu 11.04 amd64 (the one downloaded from the main ubuntu site) on an intel Mac?
Or, is the another Intel 64 version? 

I have a Macbook pro 5,3 with Lion installed.

---

### Post by majortom67 on 2011-09-08
> **jtaylor7192 said:**
> Can I install Ubuntu 11.04 amd64 (the one downloaded from the main ubuntu site) on an intel Mac?
Or, is the another Intel 64 version? 

I have a Macbook pro 5,3 with Lion installed.

"AMD64" is the distro for 64bit Intel architecture and similars (AMD) processors such as the Core 2 Duo your MacBook should have.

---

### Post by joceloon on 2011-09-08
Scratching my head over this one...I recently purchased a Macbook Pro (15" and early 2011, 8,2) and I wanted to install Ubuntu alongside Lion (I've previously installed it alongside Windows on 3 different machines with no problems). After some struggling, I finally got it to boot an 11.04 disk and successfully created a SWAP partition and an ext4 partition using space I'd allocated for Windows using Boot Camp. However, whenever I press option at startup, Ubuntu (or "Windows" as the walkthroughs say it's sometimes called) isn't displayed: I see the regular Mac HD, the Recovery HD, and three different recovery things that weren't there before (one for Snow Leopard and one for Mac and Windows, if I recover correctly). No Ubuntu, no Windows.

rEFIt also isn't working, although I've read that's a known issue. Can't dig up anything about Ubuntu just not showing up after installation, though (although my Googling skills might not be up to par). Couldn't find anything on the first 3 pages. Apologies if this has been answered elsewhere.

---

### Post by linuxdady on 2011-10-24
The solution is simple: Create a  live CD AND a live USB. The live system will boot from CD and procede from USB.
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by fiazseo on 2011-10-25
If you're saying "I've tried all the solutions in the rss feeds, and I still can't get my appear to operate the way I need" then you might try adding some of the programs talked about in this article so as to enable/disable issues.

---

### Post by russellhowes on 2011-11-03
Hi,

I realize this problem may have already been successfully addressed elsewhere...if so sorry, but if you could direct me to one of those places I would appreciate it greatly!

I have a mid-2007 (3,1) Macbook Pro on which I recently installed Ubuntu 10.04 (LTS release, it was the only one whose installation CD I could get to work) and manually upgraded to 10.10 then 11.04. The display settings see my laptop display as 'unknown' and do not recognize my external monitor at all.

I've installed the nVidia additional drivers but they don't 'activate'...I don't know whether that is a problem or not. I have found several command line hacks posted on various discussion board threads but the ones I've tried have not worked for me. Is there something simple I am missing?

---

### Post by joreg on 2011-11-30
Very cool I have analyzed some of my problems me Thank you

---

### Post by windfix on 2012-01-01
Finally, I got a working solution: Plop Linux boot manager

 [http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html)

[LIST=1]
[*]unzip and burn the iso inside the folder to a cd
[*]plug the live-usb-disk and insert the boot-cd into the computer
[*]when you start up the computer from the CD it will bring you a menu to choose which device to boot from
[*]select usb
[/LIST]

Send the author a donation via his site if this saves you as much headache as it does for me!

---

### Post by alkhemista on 2012-03-01
Just recently got 10.10(64bit) up and running on a mbp5,1! Have to say, I'm pretty impressed.

My only question: Has anyone successfully upgraded from 10.10. to 11.04 on a mbp5,1? (unibody late 2008)

---

### Post by Kyl3 on 2012-03-10
I am trying to dual boot Ubuntu on my Mac mini (version: Macmini2,1). I have been following the "Detailed How-To" instructions on [this page of the Ubuntu documentation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation").

I run into a problem at the "Fix Partition Tables" step. I get the "analysis inconclusive" message described in the second bullet point in this section of the documentation. The documentation says to follow the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185") for using gdisk to rebuild the partition table.

From a live Ubuntu CD, I followed step 1 and installed [gdisk]("http://sourceforge.net/projects/gptfdisk/").

Step 2 says to run "sudo gdisk /dev/disk0". Instructions earlier in the post say to replace "disk0" with "/dev/sda or the appropriate device". I'm sorry this is such a newbie question, but **what should I be replacing "disk0" with?**

Thank you in advance.

---

### Post by Kyl3 on 2012-04-08
Sorry to post again, but since no one is responding, I'm wondering if my question doesn't make sense or has already been answered somewhere else. Any input would be much appreciated.

---

### Post by 2F4U on 2012-04-09
I think the key information is 

> Everything that follows was done from a Mac OS terminal. 

This makes sense since /dev/disk0 is Mac notation and the poster is running this step from Max OSX.
The poster is even mentioning

> You could just as easily do steps 1-8 from the USB Live session; you  need to use /dev/sda or the appropriate device instead of /dev/disk0

So, if you are running the steps from Ubuntu, use /dev/sda instead of /dev/disk0.

---

### Post by Kyl3 on 2012-04-21
> **2F4U said:**
> So, if you are running the steps from Ubuntu, use /dev/sda instead of /dev/disk0.

The thing that's catching me up is that the instructions say "You could just as easily do steps 1-8 from the USB Live session; you need to **use /dev/sda or the appropriate device** instead of /dev/disk0." I know nothing about hard drives or partitions. I'm doing this from a live Ubuntu CD. How do I know if /dev/sda is the "appropriate device"?

Thanks.

Edit: Just for the sake of trying something, I ran the command "sudo gdisk /dev/disk". I got back "sudo: gdisk: command not found". What am I doing wrong?

---

### Post by chugtairizwan on 2012-04-23
Dude you can install Linux Ubuntu on Mac just check this link
**[http://www.youtube.com/watch?v=G0Ae1mSICO8](http://www.youtube.com/watch?v=G0Ae1mSICO8)**
**[http://www.tuaw.com/2009/09/07/how-to-set-up-ubuntu-linux-on-a-mac-its-easy-and-free/](http://www.tuaw.com/2009/09/07/how-to-set-up-ubuntu-linux-on-a-mac-its-easy-and-free/)**
best of luck

---

### Post by jonas2012 on 2012-06-09
Hello, first of all thanks for all the work you are doing/already did. This is great. 

Im just new around the corner, trying to get Ubuntu 12.04 running on a MacBookPro 5,3 for the first time and i really enjoyed making all the individual buttons work. This was imo the best part of the new experience so far.

Although i wish there would be more documentation on the more dangerous parameters, that one can accidently do as a newcomer, such as "acpi off", which was the only parameter, that i got ubuntu working with in the first place. Unfortunately i only learned of its dangers later on from a fellow on another forum.

Now i also tried other boot parameters mind you, but no one could give me instructions on how to exactly modify the file. Before the splash, after it or replace.... 

This makes it hard for newcomers. 

And sure i should have red more before attempting something like this, still i think it would be good, to add some of this info somewhere to the tutorials, until there are better ways to run this with efi 

aka

what are the boot parameters, which ones can be used safely, if it does not work on your mac, so it will initialise.

Thanks.

---

### Post by Lunarts on 2012-07-25
I have this guide on the community wiki: [https://help.ubuntu.com/community/ubuntupreciseon2011imac](https://help.ubuntu.com/community/ubuntupreciseon2011imac)

---

### Post by Eglo on 2012-12-27
Hi, had ubuntu 12.4 installed on **iMac 7,1**, everything work fine wireless, boot, sounds ..etc. some time if work with graphic like Blender, Gimp ...
become the screen like this:
[IMG]http://img338.imageshack.us/img338/7331/16962063.png[/IMG]

Dosn't work any more within reboot the system!

Hope that you solved this issue :-)




Regards
Eglo

[COLOR="Red"][B]
More details about the model:[/B][/COLOR]
> iMac "Core 2 Duo" 2.4 24-Inch (Aluminum) features a 2.4 GHz Intel "Core 2 Duo" processor (T7700), with two independent processor "cores" on a single silicon chip, a 4 MB shared level 2 cache, an 800 MHz system bus, 1 GB of RAM (667 MHz DDR2 SDRAM, PC2-5300), a 320 GB (7200 RPM) Serial ATA hard drive, a vertically-mounted slot-loading DVD+R DL "SuperDrive", ATI Radeon HD 2600 PRO graphics acceleration with 256 MB of GDDR3 memory, a built-in iSight video camera, and built-in stereo speakers underneath the 24" glossy TFT Active Matrix LCD (1920x1200 native) display designed to "bounce sound off the desk below".

Connectivity includes three USB 2.0 ports, a Firewire "400" port and a Firewire "800" port, built-in AirPort Extreme, and Gigabit Ethernet, as well as mini-DVI, which supports an external display in "extended desktop" mode.

---

### Post by Eglo on 2013-01-08
If you cant support or answer, wh's this support mean?????

---

### Post by lisati on 2013-01-08
> **Eglo said:**
> If you cant support or answer, wh's this support mean?????

This forum community is made up volunteers in mnay timezones and with a variety of knowledge. They answer questions when they can.

---

### Post by JoeBlack2k on 2013-05-04
> **Eglo said:**
> Hi, had ubuntu 12.4 installed on **iMac 7,1**, everything work fine wireless, boot, sounds ..etc. some time if work with graphic like Blender, Gimp ...
become the screen like this:
[IMG]http://img338.imageshack.us/img338/7331/16962063.png[/IMG]

Dosn't work any more within reboot the system!

Hope that you solved this issue :-)




Regards
Eglo

[COLOR="Red"][B]
More details about the model:[/B][/COLOR]


That has nothing to do with "Apple" but with the Ati Videocard.. try updating it.. Ati's support sucks though

in a terminal:
wget [http://www2.ati.com/drivers/linux/amd-catalyst-13.4-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-catalyst-13.4-linux-x86.x86_64.zip)
unzip amd-catalyst-13.4-linux-x86.x86_64.zip
chmod +x amd-catalyst-13.4-linux-x86.x86_64.run
sudo ./amd-catalyst-13.4-linux-x86.x86_64.run --buildpkg Ubuntu/quantal
sudo dpkg -i fglrx*.deb


[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by HappyLifeMachine on 2013-05-27
Hi, I recently stumbled upon a huge Nvidia Optimus problem where Bumblebee failed to load the i915 driver on a MBP 6,2. I figured out a workaround where you just install nvidia-current and blacklist i915 and nouveau to only use the Nvidia card. The MBP 6,2 wiki has no information on the i915 driver even failing (or Bumblebee for that matter) and I was wondeirng how I could edit it to add the information. I apparently do not have permission to load the edited file with added info and I don't see any place on the forums to give the info.

---

### Post by casey3 on 2013-08-25
I've got Ubuntu 12.04.2-desktop-i386 on an Intel Mac Mini from 2006 with OS X 10.4. I've installed all the updates but it's still running pretty slow. Are there any drivers I need to install, or is this a hardware issue?

---

### Post by psignosis2 on 2014-07-16
Perhaps the FAQ can be updated to reflect that booting to external drives is now possible through the use of external thunderbolt connected drives. 

Thunderbolt is basically a PCI express connection. I've read in these forums that Thunderbolt support was added to the kernel in 3.12.

I've been using the Seagate GoFlex 2.5" Thunderbolt/SATA enclosure/adapter without problem (14.04).

---

### Post by guynux on 2014-11-25
Hi, for information, installation with 64 bit images is possible on such particular Mac with **32 bit EFI/firmware** and **64 bit processor**. My iMac 6.1 with 3Go RAM works fine in unity and gnome-shell.
I have used the ubuntu-14.04.1-desktop-amd64+mac.iso burned on a DVD (no boot with USB key). All others images were only bootable in 32 bit (only DVDs).
So, providing **amd+mac 64 bit iso is mandatory** for these machines and I hope to get it for 14.10 and next.

---

### Post by Roland Lewis on 2019-09-12
> **guynux said:**
> Hi, for information, installation with 64 bit images is possible on such particular Mac with **32 bit EFI/firmware** and **64 bit processor**. My iMac 6.1 with 3Go RAM works fine in unity and gnome-shell.
I have used the ubuntu-14.04.1-desktop-amd64+mac.iso burned on a DVD (no boot with USB key). All others images were only bootable in 32 bit (only DVDs).
So, providing **amd+mac 64 bit iso is mandatory** for these machines and I hope to get it for 14.10 and next.
Yes, but that's very old advice. One can strip unnecessary entries from the El Torito catalogue and get any recent AMD64 version to boot.

Instructions can be found half-way down this page: [https://mattgadient.com/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/)

---

### Post by tvgir on 2021-02-22
Hi! How can I contribute to the iMac 2011 documentation for a modern Ubuntu version? I'd like to contribute to this page: [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

---

### Post by QIII on 2021-02-22
Given that the page you cited and [this one]("https://wiki.ubuntu.com/MactelSupportTeam") have not been updated in more than 7 years, you may have missed a boat long departed from the port.

Generally, one must be an [Ubuntu Member]("https://wiki.ubuntu.com/Membership") and further be granted rights to edit.

Becoming an Ubuntu Member is not an overnight undertaking.  A long-term demonstration of commitment and an excellent history of support or contributions will be required.

For instance, membership may be gained by [Ubuntu Forums contributions]("https://wiki.ubuntu.com/Forums/Membership").  Be aware that the minimum amount of time is just that: a minimum.  It is not likely that we on the Forums Council will move to grant membership after just six months.  Post *count* is less important that post *quality.*

The keys here are time, commitment and valuable contributions.

And now, given the advanced age and length of tooth shown by this thread:  closed.

---

