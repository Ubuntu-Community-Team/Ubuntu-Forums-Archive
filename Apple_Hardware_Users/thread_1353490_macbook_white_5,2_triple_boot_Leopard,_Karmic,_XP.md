---
title: "macbook white 5,2 triple boot: Leopard, Karmic, XP"
date: 2009-12-12
forum: Apple Hardware Users
---

### Post by neoxro on 2009-12-12
I am trying to get a triple boot to work and have ran into some problems... can anyone shine some light in my direction please?

Hardware:
[LIST]
[*]Macbook 5,2
[/LIST]
Target OS:
[LIST]
[*]OS X Leopard
[*]Ubuntu 9.10 Karmic
[*]Windows XP SP3
[/LIST]
Software:
[LIST]
[*]Leopard CD
[*]Karmic AMD64 CD (i386 did not work for me)
[*]XP SP3 CD
[*]rEFIT
[*]BootCamp
[/LIST]

**Background: Step-by-Step Log:**

Install Leopard from CD:
[LIST]
[*]Download/Install rEFIT
[*]BootCamp Partition for Windows (Leopard comes w/ BootCamp)
[*]DiskUtil Partition for Ubuntu Karmic
[/LIST]
Reboot w/ Windows XP SP3 CD:
[LIST]
[*]Install XP on **C:\** (BootCamp) w/ FAT(QUICK)
[*]Reboot into XP
[*]Install BootCamp & Mac Drivers on XP using Leopard CD
[/LIST]
Reboot w/ Ubuntu Karmic **AMD64**:
[LIST=1]
[*]Pick English
[*]F6 -> **acpi=off**
[*]Install Karmic
[*]Use advanced partition: **sda3** -> "ext3", "format", "/"
[*]No Swap Warning: OK
[*]Set Bootloader: **sda3**
[*]Reboot into **Leopard**
[*]Reboot into **Leopard** AGAIN
[*]Reboot into **rEFIT** -> **Legacy OS**
[*]Press **E** at GRUB menu
[*]Append **acpi=off** to the line that contains **/boot/vmlinuz-2.6.31-14-generic root=/dev/sda3**
[*]CTRL-X
[*]Get **medibuntu **and **mactel support** repositories
[*]Run[LIST]
[*]sudo apt-get install pommed
[*]sudo apt-get install nvidia-bl-dkms
[*]sudo apt-get install ubuntu-restricted-extras
[*]sudo apt-get install build-essential
[*]sudo apt-get install grub-efi
[/LIST]
[*]Activate Broadcom STA and NVIDIA 185 from Hardware Drivers
[*]Open Terminal
[LIST]
[*]cd /usr/lib/grub/x86_64-efi
[*]sudo grub-mkimage -d . -o grub.efi part_gpt hfsplus fat ext2 normal sh chain boot configfile
[*]sudo gedit grub.cfg
> menuentry "UBUNTU 2.6.31-14" {
# Set the root device for Linux.
fakebios
root=(hd0,3)
# Load the loader. - other options: video=vesafb noefi
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 video=efifb acpi=force
initrd /boot/initrd.img-2.6.31-14-generic
}

#keymapping: remeber these keys when you boot, they can be helpful!!!
#F1 = ctrl-x
#F2 = ctrl-a
#F3 = ctrl-e
[/LIST]
[*]Transfer /usr/lib/grub/x86_64-efi to a USB thumbdrive
[*]Reboot into Leopard
[*]Copy /x86_64-efi from USB to /efi on Macbook
[*]Reboot into rEFIT
[*]Let rEFIT remap (second small icon from the left)
[/LIST]

At this point, I have four icons in the rEFIT menu.
[LIST]
[*]Leopard
[*]Grub-efi
[*]Legacy OS
[*]XP
[/LIST]
I have no idea how to remove the unused Legacy OS icon, but all three OS are now functional per their current configuration.  My problem arises when I try to configure Windows XP to my needs.

**Issues: Step-by-Step Log:**

[LIST=1]
[*]Install Google Pack -> Spyware Doctor beeps few times about failures but the installation runs its course without crashing.
[*]Reboot into XP -> XP forces a disk check which seemed to hang, so I thought I broke it.
[*]Force shutdown (power button)
[*]Reinstall XP over current installation -> Completes without problem, and all 3 OS still seem to run.
[*]Boot into XP again
[*]Run Windows Update -> detects 61 updates and installs them, 14 updates failed to install.
[*]Reboot into XP -> XP forces a disk check.  I waited this time.
[*]XP reports bad clusters and tries to repair them (took ~1 hour)
[*]XP scans for free space (took ~1 hour)
[*]XP boots -> all seemed fine
[*]Run Apple BootCamp Update (Only BootCamp)
[*]Install Avira, Firefox, Google Chrome
[/LIST]

At this point, I thought I was going to announce a triple boot success, so I boot into Karmic to configure.
[LIST]
[*]Reboot into Ubuntu Karmic
[/LIST]
[LIST=1]
[*]First thing I noticed was a disk failing warning from Palimpsest Disk Utility.  It had found 160 bad sectors or errors and recommends a disk replacement.
[*]I immediately try to google for "palimpsest" and realized I had no internet.  (which I used to configure Karmic earlier)
[*]Network Manager detects both **auto eth0** and **auto wireless** but showed each one to be disconnected.
[*]I tried to connect to each one, but it'd try and fail with "Wired Network Disconneted" or "Wireless Network Disconnected"
[/LIST]

I have not yet googled deeper into networking, however, it seemed like it had to do with XP's actions on disk check/repair.  And what of the 160 bad sectors?  Am I to ignore that warning if I could somehow get my network back?  I am currently thinking about reinstalling the Karmic partition and will try to find a network solution.

Please let me know if you have any ideas of how and why this happened, so I could possibly narrow down my search for a solution...

Kudos: hoborider @ [http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)

---

### Post by neoxro on 2009-12-12
Further forum searching revealed that the palimpsest issue may be related to [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

I still have no clue why the network is out.

Network Manager detects wifi signals, detects there's eth0.  It distinguishes between plugged and unplugged.  It can try to connect to eth0 or wireless, but it'd just spit back out "Disconnected" after a few seconds.   None of the settings seemed to have been changed...


Since it had been working before, I don't think I'm missing any drivers or configurations...

Still unresolved...

---

### Post by linuxopjemac on 2009-12-13
I guess you can come up with this yourself, but I would begin from scratch and let XP not touch your disks.

---

### Post by neoxro on 2009-12-13
Right, that's what I thought as well.  I reinstalled both xp and karmic partition and experienced continued chkdsk problem.  Therefore, I disabled chkdsk with chkntfs, but then the problem was, xp kept messing up FAT32 and essential files kept going missing.  So then I reinstalled with NTFS, which felt much much faster, and XP hasn't complained since.   After that, I installed Karmic again, disabled palimpsest's warning messages.

I still run into minor problems sometimes with Karmic's network, which would not connect until I reset my router after booting into Karmic... ??

That's ok for now, that all 3 OS work.

---

