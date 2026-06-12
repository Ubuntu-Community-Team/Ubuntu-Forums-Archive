---
title: "How to move Live OS to HDD"
date: 2013-03-31
forum: Any Other OS
---

### Post by dorruk on 2013-03-31
Hey, this is a little bit out of ubuntu, concerning another OS installation over ubuntu, but there's nowhere else to ask this, so here goes.

Installed Chromium OS Vanilla on a USB as a Live OS. Burned the .img file using ImageWriter.
There's the screenshot from GParted of how my USB looks like. Ignore the 12 GB of unallocated space because the drive is 16 GB and the OS doesn't take up that much space.
As you can see, it's quite a mess.

The thing is, the OS is live, so I'd like to move partitions from this USB to my HDD, so I can use it forever rather than a demo stuck in a USB.
Question is, which partitions to move? And how do I move partitions? And how to add this new OS to grub?

Thanks in advance.

---

### Post by cariboo on 2013-03-31
Moved to Other O/S talk

---

### Post by dorruk on 2013-04-03
Bump.

---

### Post by oldfred on 2013-04-03
The liveCD is intended to be an installer or a way to test Ubuntu and make repairs. It is not intended to be installed to a hard drive and is not updateable, although with persistence you can save some things, but space is limited.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

      
 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by C.S.Cameron on 2013-04-03
I played with Chromium OS Vanilla a few years ago.
If I recall right it is an actual install via image and not what they call "Live".
I thought it was possible to write the image directly to HDD, perhaps an external USB HDD enclosure is required.

Otherwise I would suggest deleting all the partitions except SDC1 and SDC3 and move those to the left using gparted.

You can then use dd to overwrite everything on the hard disk with a clone of the USB drive.
You can boot from the Live CD to do this.
(This will delete all existing data on the disk).

```
sudo dd if=/dev/sdx of=/dev/sdy
```

Where x is the from device and y is the to device.

After you are done you can expand the new HDD partition using gparted.

Welcome to the Forums

---

### Post by dorruk on 2013-04-05
I ran this:
```
sudo dd if=/dev/sdc of=dev/sda8
```
in which sdc is my USB and sda8 is the target hard drive partition...

Next I updated GRUB. but it didn't recognized the OS :(

By the way, I accidentally ran update-grub while USB was mounted and it recognized the on-USB Chromium. But the on-drive Chromium wasn't listed.

In light of this information, I'm wondering if I ever missed out copying out the boot sector under the use of "dd".. Or should I have not copied the empty 512 byte partitions but only the two partitions of the USB that are 2 GB and 1 GB?

---

### Post by oldfred on 2013-04-05
dd is intended to be same size to same size exact copy. Drive to drive, partition to partition, or either to a file.
 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)


But you copied a drive to a partition and drive had two partitions? So now you have a partition with two partition structures inside it. I do not think that will work.

---

### Post by dorruk on 2013-04-05
> **oldfred said:**
> dd is intended to be same size to same size exact copy. Drive to drive, partition to partition, or either to a file.
But you copied a drive to a partition and drive had two partitions? So now you have a partition with two partition structures inside it. I do not think that will work.

According to your advice, I manually created the two biggest partitions (sdc3 and sdc1 in screenshot) and copied them with dd.
This time, grub recognized the OS. But when I opened it, the operating systems' boot screen came but the screen was mixed with a command line and the command line was working and instead of normally booting, Chromium attempted to go into something that looks like a recovery boot, so it looked pretty weird. Would post a screenshot if I could. But I think Chromium is just telling me that I need more than these two partitions to get it to work.

This time, I will create and clone copy all 12 partitions under an extended partition and will post you the results.

EDIT: Oh well, I just realized that I forgot copying the sector including the bootflag (dev/sdc12). My bad...

---

### Post by oldfred on 2013-04-05
I doubt that you need all those partitions.

Copying partitions will not copy grub in the MBR, if it uses grub as boot loader. Grub does not use boot flag, but syslinux does.

Using dd you will have duplicate UUIDs which for most systems is a problem as you cannot have duplicate UUIDs. Be sure to unplug flash so system does not see the duplicates. If you want to keep flash installed you will have to change one or the other to new UUIDs.

---

### Post by dorruk on 2013-04-06
> **oldfred said:**
> I doubt that you need all those partitions.

Copying partitions will not copy grub in the MBR, if it uses grub as boot loader. Grub does not use boot flag, but syslinux does.

Using dd you will have duplicate UUIDs which for most systems is a problem as you cannot have duplicate UUIDs. Be sure to unplug flash so system does not see the duplicates. If you want to keep flash installed you will have to change one or the other to new UUIDs.

According to this, I tried to boot while the USB is unplugged.
I have copied sdc8, sdc12, sdc5, sdc3, sdc1. in the exact order, and leaving the necessary unallocated space in between. I used the "ext2" file system when creating a corresponding partition on my HDD for sdc5 (which is an unknown file system).

Still, the OS doesn't boot normally.
Do you have an idea which partitions am I supposed to copy?

---

### Post by dorruk on 2013-04-08
> **C.S.Cameron said:**
> I played with Chromium OS Vanilla a few years ago.
If I recall right it is an actual install via image and not what they call "Live".
I thought it was possible to write the image directly to HDD, perhaps an external USB HDD enclosure is required.

Otherwise I would suggest deleting all the partitions except SDC1 and SDC3 and move those to the left using gparted.


Done that, still have that problem...

And something that I have noticed:
In sdc12, there are two folders named efi and syslinux.
On my BIOS, "EFI Mode" is off. And my bootloader is grub. But it was working well with my USB.

In means of providing further information, I have noted down errors appeared within the terminal that I could watch the boot process fail.
When system boots, it recognizes the computer parts, like naming the sound card, processor etc.

First, I see on the screen, "your system is repairing itself, please wait" for about 0,2 seconds.
Then it is being intervened by a terminal in which text begin to flow really fast.
But I managed to catch some errors..

First error is:
```
cryptohome: segfault at 8 ip 777e1c0b sp 7fa3be10 error 4 cryptohome[7777]
```
Then:
```
init: chapsd main process (1323) killed by APRT signal
init: chapsd main process ended, respawning.
```

A repeating error is:
```
init: cryptohomed-client main process (2248) terminated with status 1
init: cryptohomed main process (2251) killed by ABRT signal
init: cryptohomed main process ended, respawning
```

Numbers in parantheses are always changing.

If anybody managed to copy Chromium to their hard drive, please let me know.

---

### Post by dorruk on 2013-04-08
Since there were folders named efi and syslinux on the USB, I just made a test.

And, I have figured out that the problem is with the bootloader.
While the OS is fully installed on the USB and this USB is plugged in, I updated GRUB. So the on-USB, working Chromium distribution is now listed in my boot menu.

Then I attempted to boot the USB using GRUB, rather than booting the USB by giving BIOS hard drive priority.
It failed.

So, my assumption that the OS type is EFI was true. But in my BIOS, "EFI Mode" is off. And if I switch it on, then my legacy OSs may stop working.
Thus, my new question should be: **How do I get Chromium to serve as a legacy OS?**

---

### Post by dorruk on 2013-04-09
Bump.

---

### Post by oldfred on 2013-04-09
From a Linux repairCD/DVD/Flash you can run this. I doubt it works in Chromium. But it may show what files are where. It really parse for grub & Linux boot files, so I am not sure what it will find.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by dorruk on 2013-04-10
[http://paste.ubuntu.com/5695578/](http://paste.ubuntu.com/5695578/)

---

### Post by oldfred on 2013-04-10
Your unknown install is not configured correctly, but I do not know if changes would make it work or not. It shows it was gpt partitions, but on hard drive you have msdos. It also says it is booting from sdb3 and you have it in sda8. It also looks like it uses syslinux which is a Windows boot loader, so I do not know if direct boot of linux image would work. Also I do not understand its fstab entries. It just shows /dev/BOOT etc which may be using labels, which you do not have. You would need the three labeled partitions that it has in fstab.

---

### Post by dorruk on 2013-04-10
> **oldfred said:**
> Your unknown install is not configured correctly, but I do not know if changes would make it work or not. It shows it was gpt partitions, but on hard drive you have msdos. It also says it is booting from sdb3 and you have it in sda8. It also looks like it uses syslinux which is a Windows boot loader, so I do not know if direct boot of linux image would work. Also I do not understand its fstab entries. It just shows /dev/BOOT etc which may be using labels, which you do not have. You would need the three labeled partitions that it has in fstab.

So, what should I do now?

---

### Post by oldfred on 2013-04-10
It looks like you need three partitions, the one's label BOOT, ROOT & SWAP as it uses labels in fstab. 

The copy that you are trying to do requires a good understanding of fstab, grub or syslinux and partitions. Unless it has an installer you have to manually edit all of those settings to be correct. And even then I am not 100% sure it would work.

---

### Post by dorruk on 2013-04-11
Since I don't have that kind of expertise, should I just give up?

---

### Post by dorruk on 2013-04-13
Bump.

---

### Post by dorruk on 2013-04-20
Bump.

---

