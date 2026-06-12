---
title: "Ubuntu on External Firewire"
date: 2009-10-09
forum: Apple Hardware Users
---

### Post by SoulstormGR on 2009-10-09
My first post! :)

I am trying to install Ubuntu on my external firewire drive. My internal drive is almost filled, and I have no Windows partition inside it.

Before installation, I have formatted my external firewire drive with Disk Utility on OS X and I have selected the "GUID Partition Table" option, under "Options" but I have formatted it as "Free Space" (other options were HFS+, and Windows).

Booting from the CD and installation is going fine. The system installs as documented with no problems. In the dialog where linux asks in what partition will you install Linux, I have selected the one with the "largest continuous available space".

I have also installed rEFIt.

However, I am unable to boot from my Linux installation after installation completes. I have read many installation documentations, and people suggest that I install GRUB2. But, I am a newbie in this sort of stuff, and I have some questions:

1) Where should I install GRUB? On my Mac OS X installation or on the Linux installation?
2) Is booting from an external drive feasible or am I trying to do the impossible?

I have an Intel iMac with Core 2 Duo inside, and I am trying to install Mint, that has the Ubuntu 9.0.4 codebase (although I presume that this is irrelevant, and the problem plagues all Ubuntu versions).

Any help would be greatly appreciated.

---

### Post by pizzacake on 2009-10-09
This how I installed fedora on an external drive, must be similar for Ubuntu.  This requires you to choose the custom partitioning option.

To install ubuntu on an external drive you must create a small 200mb /boot partition on the internal hard drive.  on a mac this will look like:
efi partition	200 MB
os x partition hfs+ n GB
/boot partition	200 MB

ASSUMING EXTERNAL HDD CONNECTED!
install refit on hard drive or an external usb drive.  install ubuntu using custom partition layout with /boot on internal hard drive and lvm with /root /swap /home etc on external drive.  boot up with refit usb key using option key and select refit and select refit partition manager.  this will ask you if you want to sync partition enter y for yes.  shut down.  on next boot you will see option to boot from external drive which will be called windows.  select this and ubuntu will boot from external drive.

If you don't want to use LVM logical volume management then try this partition layout
INTERNAL HDD
/boot	format as ext2         	--install boot loader in this partition
EXTERNAL HDD
swap	format as swap area	--double system memory up to 2GB
/root	format as ext4	
/home	format as ext4                --separate /home partition is optional

---

### Post by SoulstormGR on 2009-10-09
I will try that tomorrow and I will post back with the results. Thanks!

---

### Post by SoulstormGR on 2009-10-10
> **pizzacake said:**
> This how I installed fedora on an external drive, must be similar for Ubuntu.  This requires you to choose the custom partitioning option.

To install ubuntu on an external drive you must create a small 200mb /boot partition on the internal hard drive.  on a mac this will look like:
efi partition	200 MB
os x partition hfs+ n GB
/boot partition	200 MB

ASSUMING EXTERNAL HDD CONNECTED!
install refit on hard drive or an external usb drive.  install ubuntu using custom partition layout with /boot on internal hard drive and lvm with /root /swap /home etc on external drive.  boot up with refit usb key using option key and select refit and select refit partition manager.  this will ask you if you want to sync partition enter y for yes.  shut down.  on next boot you will see option to boot from external drive which will be called windows.  select this and ubuntu will boot from external drive.

If you don't want to use LVM logical volume management then try this partition layout
INTERNAL HDD
/boot	format as ext2         	--install boot loader in this partition
EXTERNAL HDD
swap	format as swap area	--double system memory up to 2GB
/root	format as ext4	
/home	format as ext4                --separate /home partition is optional

As fas as I understand, The only difference is to make a /boot volume in the internal hard drive because rEFIt only recognizes the internal boot volume.

I only have one question: What are the sizes for the swap and /root volumes? You said about the swap to double system memory up to 2GByte. So I have a 2 GBytes RAM, must I make the swap also 2 GBytes? I don't want to use /home. Also, isn't ext4 slightly unstable when compared to ext3? Can I use ext3?

---

### Post by SoulstormGR on 2009-10-10
Unfortunately, I had no luck at all...

I installed ubuntu on my external hard disk drive. Those are my settings in the attached image.

I have installed the boot loader into my internal disk, but after rEFIt did not synced my disks because it said it was not necessary!

Also, while installing, there was no "/root" installation location, Ubuntu complained about that. I assume you meant just "/" as installation destination.

Any ideas? Must I install GRUB 2? I have been fighting with this for so many hours I think I might just leave Linux alone and run them with Fusion or some other emulation software...

---

### Post by SoulstormGR on 2009-10-10
I did it!

After carefully following your instructions, I needed to do one more thing:

I needed to boot from the LiveCD one more time, and reinstall GRUB using the instructions here:

[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

After that, I rebooted, and my Linux Mint installation worked just fine! Thank you very much for your help.

Now, on to see how to fast switch from OS X to Linux and vise versa!

---

