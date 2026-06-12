---
title: "Creating a bootable USB stick (for Mac)"
date: 2019-12-10
forum: Apple Hardware Users
---

### Post by johne53 on 2019-12-10
Has anyone here created a bootable USB stick to try out Ubuntu? I'm running on a Mac and I figured it'd be good to install Ubuntu on a USB stick, just to try it out. I followed some instructions that I found here:-

[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0)

The above link uses some 3rd party s/ware called 'Etcher' to write Ubuntu onto a USB stick (after first downloading an ISO file). Ubuntu's ISO file was huge (over 2GB) so I chose an 8GB USB stick.

But by the end of the process, Etcher had created a tiny partition on the USB stick of just 2MB (megabytes - not gigabytes). This tiny partition contains just 2 x files, called **bootx64.efi** and **grubx64.efi** and the rest of the USB stick has been left empty (in fact, unformatted).

So I'm just wondering where it's put the rest of the Ubuntu files :confused: Ubuntu can't possibly fit into 2MB but I'd be very disappointed if Etcher's written it all to my Mac's hard drive... :mad:

---

### Post by johne53 on 2019-12-10
Sorry... I've just seen a message to say that this is a chat forum and not for support.... Can someone let me know where I should have posted?

---

### Post by slickymaster on 2019-12-10
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by johne53 on 2019-12-11
I had a flash of inspiration... I took the USB stick to a totally different computer and Ubuntu still booted just fine. So (while I was in Ubuntu) I looked at the partition table. The small 2MB partition is of type **FAT-12** and is called **/dev/sdc2**. But just to the left of it there’s a 2GB partition called **/dev/sdc1** which is of a type I’d never heard of before, called [B]0x00 (bootable)

[/B]So it's looking like either Etcher (or Ubuntu maybe) has created a partition of a type that only Ubuntu can recognise.

Weird…  :confused:

---

### Post by sudodus on 2019-12-11
I think Etcher is a cloning tool like for example

- Ubuntu Startup Disk Creator - included in Ubuntu
- Disks - included in Ubuntu
- [mkusb](https://help.ubuntu.com/community/mkusb) - can be installed (like Etcher)

This means that it copies the content of the iso file exactly to the USB stick (each byte is copied directly to the device; there is no extraction to an existing file system).

This method [to create USB boot drives] works with Ubuntu iso files and the iso files of several other linux distros. These iso files are treated with the program isohybrid and are called 'hybrid iso files'.

See this link and links from it,

[help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by johne53 on 2019-12-12
> **sudodus said:**
> I think Etcher is a cloning tool

[Edit...]

This means that it copies the content of the iso file exactly to the USB stick (each byte is copied directly to the device; there is no extraction to an existing file system).


Many thanks sudodus. The problem I'm finding with Etcher is that it  only generates a 2GB partition (no matter what size USB stick I use). And although gparted can size partitions later, it won't resize the partition that it's running from (or in fact, any mounted partition).

So do you know of any software (similar to Etcher) but which would allow me to stipulate a larger partition size than 2GB?  (e.g. would UNetbootin allow this..?)

---

### Post by sudodus on 2019-12-12
I suggest that you use [**mkusb**](https://help.ubuntu.com/community/mkusb)

- not to clone (which is the standard method to make an installer, a live drive in order to install Ubuntu)

- but this time you want a  [**persistent** live drive](https://help.ubuntu.com/community/mkusb/persistent).

A persistent live drive by mkusb has

- one partition with the label 'casper-rw' and an ext4 file system, which is an overlay of the root file system in RAM, and installed programs as well as system tweaks and files saved in the standard directories (within the home directory) are saved there

- one partition with the label 'usbdata' and an NTFS file system, where you can store various data files. This partition can also be read and written by Windows, so it can be used to exchange data with computers running Windows.

The partition table can look like this:
```

parted -s "/dev/sdc" print
Model: SanDisk Ultra Fit (scsi)
Disk /dev/sdc: 61,5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 2      1049kB  2097kB  1049kB               primary  bios_grub
 3      2097kB  258MB   256MB   fat32        primary  boot, esp
 4      258MB   2360MB  2102MB               primary
 5      2360MB  42,0GB  39,6GB  ext2         primary
 1      42,0GB  61,5GB  19,5GB  ntfs         primary  msftdata

lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE "/dev/sdc"
MODEL            NAME   FSTYPE  LABEL                    MOUNTPOINT  SIZE
Ultra Fit        sdc                                                57,3G
                 |-sdc1 ntfs    usbdata                             18,2G
                 |-sdc2                                                1M
                 |-sdc3 vfat    usbboot                              244M
                 |-sdc4 iso9660 Ubuntu 18.04.3 LTS amd64               2G
                 `-sdc5 ext4    casper-rw                           36,9G

```

Edit:

- mkusb is a linux tool and cannot be used in MacOS.

- If you want to transfer files to MacOS you can format the 'usbdata' partition to FAT32.

- If you must do the job in MacOS, you can use **Unetbootin**, but it is not straightforward to make a partition for persistence. It will create a file with the name 'casper-rw' limited to 4 GiB due to the FAT32 file system. It will also be possible to store files in the FAT32 file system, which will use the whole drive.

---

### Post by sofiee on 2019-12-14
[https://itsfoss.com/create-bootable-ubuntu-usb-drive-mac-os/](https://itsfoss.com/create-bootable-ubuntu-usb-drive-mac-os/)
have you trie d this easy way?

---

### Post by shantiq on 2019-12-15
I had a 2005 Macbook I played with an awful lot and installed various OS'ses over the last few years
Here are [some tips ]("https://ubuntuforums.org/showthread.php?t=2367200")you may find useful

---

