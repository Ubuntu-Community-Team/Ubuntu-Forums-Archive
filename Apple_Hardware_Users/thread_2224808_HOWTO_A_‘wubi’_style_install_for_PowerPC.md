---
title: "HOWTO: A ‘wubi’ style install for PowerPC"
date: 2014-05-18
forum: Apple Hardware Users
---

### Post by rsavage on 2014-05-18
This post describes how to do a manual ‘wubi’ for PowerPC.  The system is installed onto a virtual disk so no repartioning/reformating etc is necessary. However, I would still recommend that you make backups of all important data before proceeding....!

Although this guide was not written for installing to an external usb drive, it is actually a good way to install a system to such a device (see the README in the /ubuntu/ppcboot directory).  I'm not going to repeat usb specific information that is provided elsewhere, so if you want to check if your device can be booted from openfirmware then have a look at the first post  here -  [http://ubuntuforums.org/showthread.php?t=2051337&p=12210973#post12210973](http://ubuntuforums.org/showthread.php?t=2051337&p=12210973#post12210973) and of course the FAQ - [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F) .

Attached are the necessary files to make this all happen.  The first thing to do is unzip the file and copy the 'ubuntu' folder onto the root of a partition.   The partition must be formated as ntfs/ext2/ext3/ext4.  If you are using FAT32 then there is a 4GB upper limit on the file size so you'll probably have to create separate root.disk, home.disk and usr.disk files.  The following will not work with an 'exotic' filesysyem like hfs/hfs+ unless you are prepared to patch the casper/lupin/debian installer packages..... 

Next, downloaded the *ubuntu PowerPC .iso file of your choice and then place that in the /ubuntu/install directory and rename it installation.iso

If the partition containing the ubuntu folder cannot be seen from openfirmware (for example it is a linux partition), then copy the /ubuntu/ppcboot/grub file to somewhere that it can be seen.  I only have linux installed on my machine so I copied it to the bootstrap partition (/dev/sda2 in the commands below).

```

sudo mount /dev/sda2 /mnt
sudo cp /ubuntu/ppcboot/grub /mnt/
sudo umount /mnt

```

The file /ubuntu/install/custom-installation/preseed.cfg will tell ubiquity (the ubuntu installer) to use the virtual disks.  It is based on a 10GB install I did with the real wubi.  I don’t think it is necessary to change the numbers in this file since we are not doing a fully automatic install, but if you have problems then this is the file to maybe make the changes in.  Additional disks can be added like so:
```

  /ubuntu/disks/root.disk 3000 4000 4000 $default_filesystem method{ format } format{ } use_filesystem{ } $default_filesystem{ } mountpoint{ / } . \
  /ubuntu/disks/swap.disk 100 256 256 linux-swap method{ swap } format{ } . \
  /ubuntu/disks/home.disk 100 1744 1744 $default_filesystem method{ format } format{ } use_filesystem{ } $default_filesystem{ } mountpoint{ /home } . \
  /ubuntu/disks/usr.disk 100 4000 4000 $default_filesystem method{ format } format{ } use_filesystem{ } $default_filesystem{ } mountpoint{ /usr } . \

```

The preseed.cfg also tells ubiquity to install the lubuntu-desktop.  If you are installing a different flavour then change the line 
```

tasksel tasksel/first multiselect lubuntu-desktop

```
Now we need to create the virtual root and swap disks.  If you do an internet search on this then you'll see dd mainly used, but in linux we can use fallocate as it is a lot faster (see [http://stackoverflow.com/questions/257844/quickly-create-a-large-file-on-a-linux-system](http://stackoverflow.com/questions/257844/quickly-create-a-large-file-on-a-linux-system) and [http://askubuntu.com/questions/47963/how-can-i-quickly-make-a-large-file](http://askubuntu.com/questions/47963/how-can-i-quickly-make-a-large-file) ):

```

cd /ubuntu/disks
sudo fallocate -l 10G root.disk
sudo fallocate -l 512m swap.disk
sudo chmod 600 swap.disk

```

The above sets up a 10GB root disk and 512MB swap disk.  Of course you  would amend the numbers to how big you want your disks to be (some guidance on swap is here [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) ).

Incidently, the old ‘lubi’ used to create sparse files for both the root and swap disks using dd, but when I ran the installer it failed on the swap disk ([https://wiki.ubuntu.com/WubiGuide#Installation_error_while_formatting_the_swap_file](https://wiki.ubuntu.com/WubiGuide#Installation_error_while_formatting_the_swap_file) ). For those trying this on HFS+, then that apparantly also doesn't support sparse files.

Now it is time to boot the CD/ISO.  For Grub reboot into openfirmware: turn on the computer and then hold down the keys control + option/alt + o + f until you see the openfirmware prompt.

If the ubuntu folder is on partition 3 of the hard disk then you need to type the command:
```

boot hd:3,\ubuntu\ppcboot\grub

```
Amend the above to wherever the grub file is located (or you copied it to e.g. boot hd:2,\grub).  

Hopefully the boot menu should appear.  Select the “Live - 32 bit” if you have a G3/G4 processor, the “Live - 64bit” if you have a G5.

The iso should boot and you should be presented with the desktop.  DO NOT click on the shortcut to install Ubuntu.  Instead, we need to disable installing the bootloader and we do this by starting ubiquity from the terminal.
```

ubiquity --no-bootloader

```
THIS IS VERY IMPORTANT.  If you don’t use the above command then ubiquity will just pick a partition (hopefully a boot partition), format it and install yaboot (which won’t be able to boot our system anway) onto it.  

At this point the install is just like any other.  You will get a message warning you that there is no bootstrap partition for yaboot, but as long as you’ve used “--no-bootloader” then this can just be ignored.

Once the installation is complete, reboot back into openfirmware and use the same command(s) that you used before to boot grub.  We have to use grub instead of yaboot here.  A different menu should appear.  Select “Linux” and the installed system should boot!

Easy!  

To follow.... how to setup so that you don’t have to boot into openfirmware [there are lots of ways to do this depending on the version of ubuntu and whether you are dual booting]. 

A basic way would be just to set the Open Firmware environment variable: e.g. for hd (partition 3)
```

sudo nvsetenv boot-device 'hd:3,\ubuntu\ppcboot\grub'

```

---

