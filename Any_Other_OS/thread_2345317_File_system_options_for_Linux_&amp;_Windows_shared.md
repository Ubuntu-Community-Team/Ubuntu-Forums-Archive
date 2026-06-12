---
title: "File system options for Linux &amp; Windows shared hard drive"
date: 2016-12-02
forum: Any Other OS
---

### Post by kc_2 on 2016-12-02
I have the following:
2 SSDs
2 HDDs

I'm going to do this:
SSD 1 = Windows (M2 type SSD)
SSD 2 = Linux (SATA type SSD)
HDDs 1+2 = shared storage (via RAID1)

I'll probably use NTFS on SSD 1, along with LVM+EXT4 on SSD 2, although am undecided on what to use on the HDDs.

I might also set up a Linux share on the Windows SSD 1, and a Windows share on the Linux SSD 2. Possibly partitions for those shares.
(Edit: then again, I might not bother, since the HDDs will be shared between both anyway.)

What are my options for file system types to use on the HDDs, that would work on both Linux and Windows?

Also, I'm guessing that I'll have to make Windows the main boot disk instead of Linux. I've reversed that before but forgot how I did that.

---

### Post by TheFu on 2016-12-02
If you boot Windows, then NTFS is the only, real, choice that allows both OSes to have read-write access.
If the system is fast enough and has sufficient RAM, perhaps running 1 of the OSes inside a virtual machine would simplify this?

---

### Post by kc_2 on 2016-12-02
I'll run VMs but not as one of the main systems. Windows for gaming. Linux to host multiple linux VMs. The shared raid drives for both Windows and Linux to use. What are the disadvantages (for Linux) to using NTFS on the shared RAIDS?

Quick edit: speaking of which, which linux distro's a good choice for the main linux system? I'll run Windows 10 Pro for gaming, and for linux, it'll be used for all normal computing purposes and as a lab for virtualization server host type things, running about a dozen VMs in an IaaS type setup. (The approx. dozen VMs will be RHEL variants, like centos or oracle's version of rhel, but the main system hosting them, I'm open to various *nix options, considering it will also double as a personal desktop (+server.))

---

### Post by TheFu on 2016-12-02
Windows RAID isn't the same as Linux RAID. Don't think these are compatible, but I don't know. Do some more research, but I would expect that wouldn't work.

RAID never replaces the needs for backups.  **There are 1,000 problems that backups solve and only 3 that RAID solves.**  RAID really only makes sense for a few purposes.
a) you want to learn how to do it, management, recover when bad things happen.
b) you need higher performance and will be striping across at least 4 disks. If performance is the goal, use a quality RAID card from LSI that has Linux support built-into the kernel.
c) you need HA, High Availability and cannot have **any** downtime.  This never applies in a home and probably only applies to about 5% of the systems inside an average business.

There are 3 types of RAID - software RAID like mdadm.  HW-RAID from a quality RAID card that does everything inside the card, Fake-RAID which is provided by motherboards, but as slow as SW-RAID AND tied to the specific MB version and firmware like HW-RAID.  I honestly cannot think of **any** good reason to use Fake-RAID.  SW-RAID is extremely flexible and not tied to any specific hardware. I've moved SW-RAID between 3 different physical systems without any issues.  I've upgraded SW-RAID disks from 120G --> 320G --> 2TB individual disks over the years.  HW-RAID is expensive because if you can't buy 2 identical RAID cards (1 for a spare) then you don't have **any** excuse to use RAID inside a business.  There are just enough issues with RAID to make it a hassle. Search these forums to see all the people who got into a situation that wasn't easily solved.  
OTOH, RAID can handle simple issues, nicely, in an ideal world.  Last fall, a cheap Seagate 2T disk failed on one of my home servers running about 15 VMs.  The VMs kept working, as expected and I was notified via email of the degraded RAID set.  It wasn't convenient to get at immediately, but later that day I did the research, determined exactly which disk had failed (that machine has 10 disks int/ext-array, so it isn't always easy), then pulled the disk.  Ran some tests on it using another machine and sure enough, my last ever Seagate had died 25 months after purchase (the 1st in that set [I always buy 2] failed 13 months after purchase). Anyway, picked up a Toshiba 2TB on the way home the following day and a few days later, during an approved maintenance window, took down the machine and external array, added the new disk, brought everything up and added the new disk to a RAID10 setup. It is running today. No issues.

None of this removes the need for backups. There are situations with RAID where it is easier to start over with a fresh RAID-set and restore from backups.

I don't have any idea how to make RAID on Linux work with RAID on Windows. Perhaps with Fake-RAID it is possible? I dunno.

If you are running RHEL variants, why use Ubuntu?
I wouldn't run any GUI on a VM host, just sayin'.

---

### Post by oldfred on 2016-12-02
Is hardware UEFI or BIOS?
Are you installing Windows in UEFI or BIOS? Then Linux needs to be in same boot mode.
For both Windows & Linux how you boot install media UEFI or BIOS, it then the mode the install will be in. Make sure then that boot settings in UEFI/BIOS match how you installed.

---

### Post by kc_2 on 2016-12-03
The raid isn't serving as backups, I have externals for that. The raid's for reliability of immediately accessible data, lose a drive, replace a drive without losing data. I'm thinking about just using Ubuntu as the main linux system, the RHEL variants will only be for the VMs (for business practice purposes). The VMs won't have GUIs, I already have those setups essentially planned out, it's just the virtualization host that I haven't yet. lol What version of ubuntu would be good for that? To function as both a server hosting the VMs and as a personal desktop? Just plain, normal Ubuntu or one is there a server version that can also be adjusted for some personal computing purposes?

The raid will have to work on both windows and linux. I've done it before, but it has been a very long time, I forgot how I did it. Old computer that has long since had its funeral. No idea what file system to use. It will likely be a *nix-based fs, perhaps using the mdadm soft raid option. I might just have to use a 3rd party tool in windows to access it.

---

### Post by kc_2 on 2016-12-03
> **oldfred said:**
> Is hardware UEFI or BIOS?
Are you installing Windows in UEFI or BIOS? Then Linux needs to be in same boot mode.
For both Windows & Linux how you boot install media UEFI or BIOS, it then the mode the install will be in. Make sure then that boot settings in UEFI/BIOS match how you installed.

UEFI
Could you explain what you mean by the rest of your message? It's a big confusing.

---

### Post by TheFu on 2016-12-03
I install Ubuntu Server on my VM hosts, but at the core, there isn't anything special between server and desktop versions. Just different default packages and a few different default settings.  

In a business, running VMs, tuning the kernel based on the workload is still required.  Lots of guides for that.  Adding a GUI just uses more resources and introduces instabilities that X/Windows (or Wayland) provide. It isn't as bad as it was a few decades ago, but now it is habit NOT to have any GUI on a server where great stability is desired.

Did not know that Windows had a way to access both Linux software RAID and modern file systems deployed today like ZFS or BTRFS or even ext4.  I wouldn't use any other file system on a VM host.
Found this: [https://askubuntu.com/questions/59019/how-can-i-access-an-ubuntu-raid-device-from-windows](https://askubuntu.com/questions/59019/how-can-i-access-an-ubuntu-raid-device-from-windows)

---

### Post by kc_2 on 2016-12-03
Interesting! I was going to boot Windows only for gaming (still will), but was going to boot Linux for both GUI & server virtualization hosting... I will still do that, but I'll change the modes. Since I'm going to use Linux for all of my normal computing, I'll use it with GUI for that; and when I use Linux for server hosting, I'll run it without the GUI. Now I just need to figure out a good way to do that. Any ideas?

ZFS as in Solaris' with zones and all of that? Is BTRFS officially out yet? I'm a bit behind the times with the new filesystems.

So basically what I'm looking at, and this might actually change which filesystem I use for the main linux OS disk, is to run all the server/hosting/VM/etc. things on the main linux disk (which is a SATA SSD), and to use the separate RAID disks to store everything else. That storage will be used for VM storage and any extra stuff, but also for normal computing when using GUI/workstation stuff.

What would be a good filesystem to use on the linux SSD with the main system and VMs, and a good filesystem to use on the storage HDDs?

Are ZFS and BTRFS good for normal workstation purposes as well as server hosting (on the OS SSD)? Or would EXT4 be better for the multi-purpose type setup?

Using a different filesystem on SSD and HDD is okay right?

I saw that link you posted, I'm not going to run Windows as a VM, I need to use it as a physical, so it can use all of the hardware when gaming. I will eventually have a NAS setup separate from this, that'll wait 'til I built a dedicated server (possibly going the OpenStack route) but I can't do that just yet. (budget)

It would be nice if I could use the RAID + partition windows fs & linux fs, but that wouldn't work if only one system would even recognize the raid. dang, I need to look up how I did that before, it worked, just forgot how I set it up. I used 3 RAID5 HDDs, used soft raid / mdadm, and used the drives from the main OS disk (with both windows & linux).

---

### Post by oldfred on 2016-12-03
If using UEFI, install Windows to Windows drive, but be sure to boot Windows installer in UEFI mode.
Windows has requirements for lots of partitions with gpt, so let it partition Windows drive.

But better to partition Linux drive. And include the ESP - efi system partition at beginning of drive even though it will not be used inti ally. Grub only installs to ESP on drive seen as sda, so it will add a folder to the Windows drive's ESP.

Be sure to install drives in SATA port order, with Windows drive in SATA0.
If you skip a port or do not use first port your devices may change. While booting uses UUID & GUIDs which do not change anything using device /dev/sdb may change.

---

### Post by kc_2 on 2016-12-03
> **oldfred said:**
> If using UEFI, install Windows to Windows drive, but be sure to boot Windows installer in UEFI mode.
Windows has requirements for lots of partitions with gpt, so let it partition Windows drive.

But better to partition Linux drive. And include the ESP - efi system partition at beginning of drive even though it will not be used inti ally. Grub only installs to ESP on drive seen as sda, so it will add a folder to the Windows drive's ESP.

Be sure to install drives in SATA port order, with Windows drive in SATA0.
If you skip a port or do not use first port your devices may change. While booting uses UUID & GUIDs which do not change anything using device /dev/sdb may change.

I used Rufus to set up the USB with the Windows ISO, just used default settings on it, I think it included UEFI. To boot installer UEFI, I go into mobo bios and set to uefi? I think it might be uefi by default? It's a new ASUS z170 pro. I didn't know Windows requires lots of partitions, interesting. I saw a video with a guy installing windows 10, he said delete that extra partition and let windows install with the 1 partition and do its thing.

I will definitely partition the Linux drive. ESP? Interesting, never heard of it. Oh wait, so are you saying install windows 1st, then linux, with windows as the main boot, or the other way around, or something else? (with ESP requirements)

Sounds like windows is 1st, in sata 0. I'd like to boot linux first, like on the old computer, but I forgot what I did to flipflop that setting, and don't know if it would cause any problems with windows being stubborn and wanting to have priority to boot.

---

### Post by oldfred on 2016-12-03
There are three boot modes with new computers.
UEFI with Secure Boot, standard UEFI, and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
But the mode you boot USB flash drive in can be any of those modes, but system may not be set to boot with that mode. The flash drive boot and system boot modes must match.

On my Asus Z97, Secure boot was really "Windows" or "Other". Notes said use "Other" if Windows 7 as Windows 7 does not support Secure boot.
And I only could get flash drive to boot in UEFI mode, with UEFI only setting. Even UEFI and/or BIOS/CSM only booted in BIOS mode.
You should see two boot options for a flash drive if Secure boot is off. You may get no USB options if secure boot is on. USB boot is not secure. But you may then be able to specifically allow USB boot with secure boot on with other USB settings.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--]("https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference") 
    
Lots more UEFI info in link in my signature, below.

I have to document most UEFI/BIOS settings as every UEFI update resets back to defaults.

---

### Post by kc_2 on 2016-12-03
> **oldfred said:**
> There are three boot modes with new computers.
UEFI with Secure Boot, standard UEFI, and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
But the mode you boot USB flash drive in can be any of those modes, but system may not be set to boot with that mode. The flash drive boot and system boot modes must match.

On my Asus Z97, Secure boot was really "Windows" or "Other". Notes said use "Other" if Windows 7 as Windows 7 does not support Secure boot.
And I only could get flash drive to boot in UEFI mode, with UEFI only setting. Even UEFI and/or BIOS/CSM only booted in BIOS mode.
You should see two boot options for a flash drive if Secure boot is off. You may get no USB options if secure boot is on. USB boot is not secure. But you may then be able to specifically allow USB boot with secure boot on with other USB settings.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--]("https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference") 
    
Lots more UEFI info in link in my signature, below.

I have to document most UEFI/BIOS settings as every UEFI update resets back to defaults.

A fresh Windows 10 install would take care of any partitioning on its own, right?

The very first step involving partitions that I'm particularly curious about is this:
[https://www.youtube.com/watch?v=yXTqz3Fd28M&t=7m17s](https://www.youtube.com/watch?v=yXTqz3Fd28M&t=7m17s)

In that video, he finds a couple partitions already present, he deletes extras so only 1 is available to install Windows onto.

Before installing Windows & Linux, when I finish building the computer and initially boot up into BIOS/UEFI, I thought I would just make sure it's set to UEFI. And that it's not supposed to use the traditional BIOS or CSM. If there are multiple UEFI options, how do I know which one to use?

I'll re-setup the USB flash drive to match the appropriate UEFI setting that I'll end up using on the computer.

Rufus app lets me use one of these:
A) MBR partition scheme for BIOS or UEFI
B) MBR partition scheme for UEFI
C) GPT partition scheme for UEFI

Not sure which one to use.

Along those lines, does it matter if I set the computer to use Windows or Linux as the primary, the actual system that boots when powering on the computer?

Edit - the mobo:
Asus Z170-PRO ATX LGA1151 Motherboard

---

### Post by oldfred on 2016-12-03
Rufus is just setting partitions on USB flash drive. That really should not matter, although a few  systems seem to have issues with one partition scheme or the other.

I cannot follow videos, but if using only one partition that would be a BIOS/MBR without the typical 100MB boot partition. Windows in BIOS mode has to use MBR(msdos) and typically uses two of the primary partitions.

Do not confusing BIOS/MBR instructions with UEFI/gpt instructions. Pick which way you are installing and only use instructions for that method.

Windows will create the partitions it needs.
It should not matter which system you have as default boot in UEFI, you can easily change.
But many default to Ubuntu/grub as then you can dual boot from grub menu if both systems are in same boot mode and Secure boot is off.

Once Windows is installed make sure its fast start up is off. That is different than the fast boot in UEFI that probably should be off until system fully configured. My Asus allowed an adjustable delay on boot, so I set that to 3 sec just to have time to get into UEFI in case I need to make changes. Fast boot skips checks for hardware or software configuration changes and assumes system is exactly as previous cold boot.

---

### Post by kc_2 on 2016-12-03
> **oldfred said:**
> Rufus is just setting partitions on USB flash drive. That really should not matter, although a few systems seem to have issues with one partition scheme or the other.

It doesn't matter if I use MBR/UEFI or GPT/UEFI?

> I cannot follow videos, but if using only one partition that would be a BIOS/MBR without the typical 100MB boot partition. Windows in BIOS mode has to use MBR(msdos) and typically uses two of the primary partitions.

I was talking about this:


[http://i.imgur.com/qybZXrs.png](http://i.imgur.com/qybZXrs.png)
[IMG]http://i.imgur.com/qybZXrs.png[/IMG]


[http://i.imgur.com/qoTTuLr.png](http://i.imgur.com/qoTTuLr.png)
[IMG]http://i.imgur.com/qoTTuLr.png[/IMG]

He deleted unallocated space so all would be used.

> Do not confusing BIOS/MBR instructions with UEFI/gpt instructions. Pick which way you are installing and only use instructions for that method.

The confusing part with that is that Rufus allows for MBR/UEFI and GPT/UEFI.

> Windows will create the partitions it needs.
It should not matter which system you have as default boot in UEFI, you can easily change.
But many default to Ubuntu/grub as then you can dual boot from grub menu if both systems are in same boot mode and Secure boot is off.

Okay I need to keep secure boot off. Good to know.

> Once Windows is installed make sure its fast start up is off. That is different than the fast boot in UEFI that probably should be off until system fully configured. My Asus allowed an adjustable delay on boot, so I set that to 3 sec just to have time to get into UEFI in case I need to make changes. Fast boot skips checks for hardware or software configuration changes and assumes system is exactly as previous cold boot.

I'll disable fast start up and fast boot. Setting 3 seconds is a good idea.

---

### Post by oldfred on 2016-12-03
Rufus is only creating the installer. The flash drive, not the partitions on the SSD.
The install flash drive is always FAT32, and UEFI can boot that with either UEFI or BIOS if configured correctly. So partition type of flash drive does not matter.

But whether gpt or MBR matters greatly with install to SSD or HDD. Windows is very particular. Ubuntu will boot in either UEFI or BIOS from gpt.
But both Ubuntu & Windows use MBR for BIOS boot.

Again how you the the installer flash drive UEFI or BIOS is then how it will install.

---

### Post by kc_2 on 2016-12-03
> **oldfred said:**
> Rufus is only creating the installer. The flash drive, not the partitions on the SSD.
The install flash drive is always FAT32, and UEFI can boot that with either UEFI or BIOS if configured correctly. So partition type of flash drive does not matter.

But whether gpt or MBR matters greatly with install to SSD or HDD. Windows is very particular. Ubuntu will boot in either UEFI or BIOS from gpt.
But both Ubuntu & Windows use MBR for BIOS boot.

Again how you the the installer flash drive UEFI or BIOS is then how it will install.

I ended up using this, and found on google search that this Rufus option for Windows 10 works:
"MBR partition scheme for BIOS or UEFI"

So I guess that will check for either setting. It's the recommended choice at least.

Right now I'm trying to figure out how to use RAID1 between 2 HDDs, and how to partition that, so half is Linux and half is Windows.

...but I am going to install Windows (on an SSD) and Linux (on another SSD) first, then mess with the HDDs.

---

### Post by JayKay3OOO on 2016-12-05
Buy or build a nas. This will be low powered so will be on all of the time and both linux and windows will be able to write to it. Gigabit ethernet link to it and you're set.

I've got a linux based nas in raid 1 that's on all the time. Uses hardly any power. 

Let me know if your interesting sollution works though. I think I've been down this path before and failed. I know you can read from EXt4 partitions by installing some 3rd party tool on Windows though, but not sure about writing and if the raid is software based it's going to need windows or linux to be on. Raid cards are pricey.

---

