---
title: "partitioning MacBook Pro disk"
date: 2013-01-16
forum: Apple Hardware Users
---

### Post by kernco on 2013-01-16
I'm trying to set up dual-boot on my MacBook Pro, and have run into some questions. I used Disk Utility to allocate some free space for Ubuntu, and now I'm in the Ubuntu installer's partitioner. 

There are already 3 partitions on my disk. One is EFI, one is for Mac OS X, and one is I think for recovery. I want to make a partition for Ubuntu and a swap partition. First I created both as primary partitions, then remembered I can only have 4 primary partitions, so I made the swap partition logical. But why did it let me set them both as primary in the first place? Does this mean one of the existing Mac partitions is logical? Or would it have messed up if I'd continued like that? Is there any disadvantage to making the swap partition logical?

My next question is about the bootloader. Since Macs use EFI not a BIOS, I read that I shouldn't install the bootloader on my MBR, which I assume is the /dev/sda choice. Instead, I changed it to /dev/sda4 which is my Ubuntu partition. I got a dialog that "The partition table format in use on your disks normally requires you to create a separate partition for boot loader code...". Should I continue or do I need to change something? I have installed rEFIt.

---

### Post by dan5schroeder on 2013-01-17
I had previously set up a dual-boot of OS X and 11.10 on a MBP 8,2 and recently decided to switch to 12.04 by reinstalling. I just did the reinstall earlier tonight (I found this thread while searching about the same "The partition table format..." warning).

I decided to go ahead and install grub to /dev/sda, because I had done this back when I installed 11.10, and (despite the warnings I've seen) it has worked for me. After the 12.04 install finished and I rebooted, rEFIt showed a "Linux" entry, picking it brought up grub, and Ubuntu booted successfully.

It's possible that it went smoothly for me because of the previous install; when I first shrunk the OS X partition to install 11.10, I did have troubles with the partition tables becoming out of sync, but I know that when I eventually got everything working, the solution involved installing grub to /dev/sda.

I make no promises this will work for you, and if anyone with more knowledge about hybrid partition tables looks at this, I'd be curious to know why many guides recommend against installing the bootloader to the MBR, but anyways, that's how this worked out for me.

---

### Post by hyalinus on 2013-01-19
I dont kbow the answer but i have the same problem and need help with my dual boot.

I have found a guide at [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

And it says:

"
Back on the Ubuntu LiveCD desktop, start the Ubuntu Installer from the desktop icon. When prompted, choose to manually partition. Select the EXT4 partition and click change. Select to use the space as the EXT4 filesystem and root (/) as the mount point. You will also want to check the box to format the partition. On the last dialog of the installer, be sure to click the “Advanced” button and choose to install the boot loader (grub) to your root Ubuntu partition, for example /dev/sda3. This will be the only partition with the EXT4 file system.
"
So i think you should install to the ubuntu partition but i really dont know.

---

