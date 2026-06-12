---
title: "Setting up single-boot *buntu 16.04 with EFI on late 2006 Macbook 2,1"
date: 2016-11-20
forum: Apple Hardware Users
---

### Post by vemacs on 2016-11-20
I had to use quite a bit of trial-and-error and combinations of random guides on the internet to get Xubuntu 16.04 working properly on my Macbook 2,1, so here's a quick overview of what needs to be done.

Here is the main guide (bench's guide) I followed, with the only difference being the installation process (as I couldn't get rEFInd to find my xubuntu flash drive):
[https://ubuntuforums.org/showthread.php?t=2287767](https://ubuntuforums.org/showthread.php?t=2287767)

Here's the heeris guide which bench's guide cites: [http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/#fixing-efi](http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/#fixing-efi)

**Installation**

This had quite a few hoops. I managed to get it working by formatting my flash drive as FAT32, putting bootIA32.efi ([http://www.mediafire.com/file/dpgorsfdkf6nn2c/ISO-2-USB+EFI-Booter+for+Mac+0.01+beta+-+Ubuntu+10.10+Live.zip](http://www.mediafire.com/file/dpgorsfdkf6nn2c/ISO-2-USB+EFI-Booter+for+Mac+0.01+beta+-+Ubuntu+10.10+Live.zip)) in EFI/BOOT, and putting my xubuntu ISO as EFI/BOOT/boot.iso.

Then, I could boot into a Xubuntu live environment off of my flash drive. Once in, I backed up /System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport from the OS X install, zeroed the partition tables with 

dd if=/dev/zero of=/dev/sda bs=16M count=64

and started the installation. I did a custom partitioning setup with a 94MB grub_boot partition (this doesn't really matter at all, it just needs to be there), a 79GB primary OS partition mounted at /, and a 4GB swap partition. I then ran the installation, and shut down the Macbook when the installer crashed when grub install failed. Then, I wrote rEFInd on my flash drive, booted off of the flash drive, and used it to select my Xubuntu install (which was somehow detected). From there, I followed heeris' guide for fixing the EFI (entirely ignoring the verification parts, they don't matter):

sudo gdisk /dev/sda
d
1
n
1
{enter}
{enter}
AF00
w

I then ran the mkfs.hfsplus step, and then did some different things with the fstab step.

There was no /boot/efi line in my fstab as grub attempted to install via bios, so I deleted a grub_boot line from my existing fstab (it was the only line other than the sda2 primary and sda3 swap lines). Then, I ran 

sudo bash -c 'echo $(blkid -o export -s UUID /dev/sda1) /boot/efi auto defaults 0 0 >> /etc/fstab'

and then reopened /etc/fstab, deleting the DEVID= part in the new line. After that, I ran

mkdir /boot/efi
sudo mount /boot/efi

And /dev/sda1 appeared to mount as /boot/efi properly (I checked via df -h). Then, I followed the "Installing Grub" section from the heeris guide (with the fake mach_kernel stuff) up until the actual grub-install part, which I used bench's guide for (linked above). It succeeded without any errors or warnings, so I unplugged my rEFInd flash drive and rebooted the computer. It successfully loaded grub and booted with minimal delay, and everything seemed to be mostly working from that point.

**Fixing wifi on resume**

Wifi is broken after resuming from suspend. I fixed that by making /etc/pm/config.d/config with contents SUSPEND_MODULES="ath9k wls1" and running sudo service network-manager restart. That fixed wifi after resuming, and also dramatically sped up the time it took to suspend.

**Fixing webcam**

I followed the Apple iSight guide ([https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)) using the AppleUSBVideoSupport I backed up earlier.

**Misc tweaks**

I had palm rejection issues with the trackpad, so I used XFCE's touchpad configuration option and set "Disable touchpad while typing" to 0.1s (there should be a similar option for Ubuntu). To improve snappiness, I ran sudo apt-get install zram-config.

---

