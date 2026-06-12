---
title: "Booting intel Apple hardware from external disk"
date: 2013-04-02
forum: Apple Hardware Users
---

### Post by pindar on 2013-04-02
Maybe the following hints will be of interest or even use to someone out there. I see questions about similar topics in the forum quite a lot, so I wanted to summarize my experience. I have an iMac 2011, and I wanted to run linux on it, but without installing it to the internal hard disk. I found the Apple setup with a hidden "restore" partition valuable and didn't want to destroy it, and I had seen that quite a few linux distributions (yes, I'm looking at you, Ubuntu!) tend to install their own bootloaders to the root of your main hard disk even though you tell them not to, making it hard to boot back into OS X. So my goal was simple: install linux on an external (firewire, but might as well be USB; thunderbolt doesn't work yet, I believe) disk without touching the OS X installation. Most of the information you see here is available somewhere on the web, but it's sometimes difficult to hunt all the details down. So here's an outline of the steps involved: 

**1.** While your computer is running (OS X, obviously, since you haven't installed linux yet), connect your brand new firewire disk to it. Open up "Disk Utility" (in the "Applications/Utilities" menu) and choose to partition the disk. And now you have to be careful: under "Options," select "GUID Partition Table." Choose to make the entire disk one partition; it doesn't matter which format you choose because we will reformat the partition later.

**2.** Now boot into your linux live system (CD or USB drive or whatever you want). If you open up a tool such as gparted, you'll see that Disk Utility has, in fact, created *two* partitions: one "EFI System Partition" of type fat 32, size 210 MB, and your primary partition. For the time being, we leave the EFI System Partition alone. We choose to delete the second (main) partition, and now we partition the hard drive to our heart's content. If you want more than one linux system on this drive, make as many additional partitions. I find it convenient to have one partition where all data resides that I share across different linux systems; this partition can then be mounted and files can be symlinked. You may also want to add a partition of type "swap" somewhere which all linux systems can share. Take mental or physical note of your partition setup; you will have to be aware of which partition is what once you launch a linux installer.

**3.** If you're running a Ubuntu live CD, you will need to install the package grub-efi:
```
sudo apt-get install grub-efi
```

**4.** Now comes the most important part: mount the first partition (the EFI System partition) to some directory:

first, find out the device number of your firewire or USB disk:

```
sudo parted -l
```

Here is an example of the output you will see for a hard disk which has been properly partitioned: 

```
Model: Maxtor 7 Y250M0 (scsi)
Disk /dev/sdd: 251GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      20.5kB  210MB   210MB   fat32           EFI System Partition  boot
 2      211MB   60.2GB  60.0GB  ext4            LINUX1
 3      60.2GB  120GB   60.0GB  ext4            LINUX2
 4      120GB   186GB   66.0GB  ext4            LINUX3
 5      186GB   246GB   60.0GB  ext4		LINUX4
 6      246GB   251GB   4791MB  linux-swap(v1)  LINUXSWAP
```

We see that the drive has the proper partition table (gpt). There are four partitions of type ext4 which can hold a linux system, and one swap partition. Take note of the device name (in our case: "/dev/sdd"); you will need to know it later.

**5.** We will now install the necessary files onto the first partition. We first have to mount it:

```
mkdir /tmp/usb
mount /dev/sdd1 /tmp/usb
```

Install the grub boot image and the necessary files on this disk (I don't know if all the modules are necessary, but having them won't hurt, it will just make your file a bit bigger). Use the device name you have seen in step 4.
```

sudo grub-install --efi-directory=/tmp/usb --boot-directory=/tmp/usb/EFI --modules="efi_gop linux multiboot part_gpt part_apple part_msdos hfsplus fat ext2 ls normal chain boot configfile ohci loopback linux search iso9660" /dev/sdd
```

After this, you will have the following directories on your partition:
```
/tmp/usb/EFI/grub
/tmp/usb/EFI/ubuntu
```

In order for the OS X bootloader to recognize the files in these directories, we will have to rename them:

```
cd /tmp/usb/EFI
sudo mv grub BOOT
sudo mv ubuntu/grubx64.efi ./BOOT/BOOTX64.EFI
sudo rmdir ubuntu 
```

**6.** We are now ready to install our linux distribution to one of the new partitions. Start the installer and choose one of those partitions as the target (mountpoint "/"). *Important*: most linux installers will at one point give you a choice where to install the bootloader. It is safe to choose not to install a bootloader at all. If the installer insists on installing one (sometimes, it's not possible to simply skip this step), choose to install it to the root partition of your installation, *not* the MBR of the disk.

**7.** Finally, in order to simplify booting from this hard disk, we write a grub2 configuration file. Assuming your EFI partition is still mounted under /tmp/usb, do this:

```
sudo touch /tmp/usb/BOOT/grub.cfg
```

Then, open this new file in your favorite text editor and add a menu entry for your new linux installation. Here is an example for a ubuntu installation:

```
menuentry "ubuntu" {
	set root=(hd1,gpt2)
	linux /boot/vmlinuz-3.5.0-26-generic i915.blacklist=1 root=UUID=XXX
	initrd /boot/initrd.img-3.5.0-26-generic
}
```

The "set root" line expects the root partition of your linux installation in EFI format; since you will boot off of this disk, it should be "hd1" and then the partition number "gptX." For the "linux" line, you will need to give the exact name of the kernel (= vmlinuz) file which you want to boot. For the root parameter, it is important to give this parameter with a UUID notation (which you find out with the command "blkid") since the device names are often unstable when you boot Apple hardware (many iMac models have an SDHC card reader, and the external disk may be /dev/sdc or /dev/sdb; sometimes even /dev/sda), but the UUID is always the same. The "i915.blacklist=1" parameter is because of a bug in ubuntu.

**8.** Some pretty random observations:
Some linux distributions will not boot immediately from fw disk. Here's a number of things you can try, in ascending order of complexity:
[LIST=1]
[*]as mentioned above, ubuntu 12.10 has an incompatibility with framebuffer devices; it needs i915.blacklist=1 as kernel parameter.
[*]sometimes, the boot process needs to wait a few seconds for the external disk to be properly connected to system. Add the kernel parameter "rootdelay=15" (sometimes "scandelay=15") to the kernel parameters in the "linux" line of he menu entry.
[*]Sometimes, this wait for the root filesystem has to be be integrated into the intrd (this is the case for slackware and its derivatives). In this case, you'll have to chroot into your new system and create an initrd with the proper parameter.
[*]If you're really out of luck, your distribution will need a custom kernel &#8211; not all have kernels which support booting from firewire disks and/or gpt partitions. If you're stubborn enough to continue, you will have to chroot into the system and compile a kernel with proper options.
[/LIST]

If you follow these steps, you should be able to boot into linux by holding the "alt" ("option") key on your Apple keyboard while powering your computer on. You should see an icon with a Firewire disk and the caption "EFI Boot." Choosing it will bring up the grub menu, where you can choose to boot into ubuntu or any other linux distribution you have installed.

---

