---
title: "How to I locate and navigate to my USB memory stick in the terminal"
date: 2011-10-10
forum: Any Other OS
---

### Post by hashes on 2011-10-10
I guess this as beginner as you can get. I have put my USB stick into the laptop so I can transfer a few files to it. Can I navigate to it? No. Can I find it? No.
 
I have googled different ways to express this. Tried many options. Nothing works. I have tried "media" and see only the cdrom. I have checked the fstab without any findings. I have tried "locate usb" only to see hundreds of lines of text passing me by.
I have tried man pages and mount... umount etc.
 
When I do find linux information, I write it down and learn it so I don't have to ask the same question twice.
 
Because of some error in BackTrack, (which I believe is close to the normal Ubuntu), I can only use the terminal and not GUI. Which is ok for now, because I need to get familar with it.
 
So where on my system is the USB to be found?
And if not found, how do I mount it?
 
Any help would be appreciated.

---

### Post by collisionystm on 2011-10-10
> **hashes said:**
> I guess this as beginner as you can get. I have put my USB stick into the laptop so I can transfer a few files to it. Can I navigate to it? No. Can I find it? No.
 
I have googled different ways to express this. Tried many options. Nothing works. I have tried "media" and see only the cdrom. I have checked the fstab without any findings. I have tried "locate usb" only to see hundreds of lines of text passing me by.
I have tried man pages and mount... umount etc.
 
When I do find linux information, I write it down and learn it so I don't have to ask the same question twice.
 
Because of some error in BackTrack, (which I believe is close to the normal Ubuntu), I can only use the terminal and not GUI. Which is ok for now, because I need to get familar with it.
 
So where on my system is the USB to be found?
And if not found, how do I mount it?
 
Any help would be appreciated.


Open Terminal.

Unplug your USB and plug it back in

right after, type dmesg

What is the output? You should see things about your USB and hopefully why it fails to mount.

---

### Post by lkraemer on 2011-10-10
Try this for more information.  Open a Terminal Window (Console) and
type the following commands:
```

lsusb
dmesg | tail

```
Then plug in your USB Flash Drive, wait a minute and retype the above commands.  Your USB device should be shown.  As an example mine was:
```

larry@debian:~$ dmesg | tail
[ 2239.134041] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 2239.137021] sd 6:0:0:0: [sdb] 7897088 512-byte logical blocks: (4.04 GB/3.76 GiB)
[ 2239.138238] sd 6:0:0:0: [sdb] Write Protect is off
[ 2239.138244] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 2239.138249] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2239.140853] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2239.140861]  sdb: sdb1
[ 2239.272677] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2239.272685] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 2239.723391] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
larry@debian:~$

```
Depending on the File Format of your USB Flash Drive, it might not be automatically mounted.  In my example my USB Flash Drive is /dev/sdb
and if I run gparted, I can verify that information and I can determine the format of the partition.

You can also use:
```

lsusb -v -d 4381:0165

```
to get more information.
```

larry@debian:~$ lsusb
Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
larry@debian:~$ lsusb
**Bus 002 Device 005: ID 4381:0165  **
Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
larry@debian:~$ lsusb -v -d **4381:0165**

Bus 002 Device 005: ID 4381:0165  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x4381 
  idProduct          0x0165 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               8
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
larry@debian:~$

```
Once the USB Flash Drive is mounted you should be able to access it via the Terminal or GUI.  Just be sure
to un-mount it before removing the physical device.  Check out the mount command with:
```

man mount

```


lk

---

### Post by nothingspecial on 2011-10-10
Moved to Other OS/Distro Talk.

---

### Post by WasMeHere on 2011-10-10
And if you want to relax for a while and use a GUI system, download some iso files and try Ubuntu and Linux Mint (based on Ubuntu)! These systems usually run very well as live systems from a boot CD or USB stick. Make the boot USB with Unetbootin

Have fun
Olle

---

### Post by matt_symes on 2011-10-10
Hi

If it has auto mounted but you are not sure where then you can check /etc/mtab

```
grep "/dev" /etc/mtab
```You can run that command before and after you insert the pen drive. Any new lines that appear will tell you the device name and where it has been auto mounted.

```
matthew@matthew-laptop:~$ grep "/dev" /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda7 /home ext4 rw 0 0
/dev/sda16 /home/matthew/my_virtual_machines ext4 rw 0 0
/dev/sda8 /home/matthew/my_documents ext4 rw 0 0
/dev/sda5 /home/matthew/my_storage ext4 rw 0 0
[COLOR=Red]/dev/sdb1[/COLOR] [COLOR=Green]/media/My_Passport[/COLOR] fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
matthew@matthew-laptop:~$
```This is for my passport. The device name is in red and its mount point is in green.

So from the terminal i would copy file into /media/My_Passport. It is case sensitive.

EDIT: This command is even better

```
grep "^/" /etc/mtab
```

Kind regards

---

### Post by el_koraco on 2011-10-10
Insert the disk, run 

sudo fdisk -l

Among others, you'll see something like

 ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   83  Linux
/dev/sda2            1216       30402   234431489    5  Extended
/dev/sda5            1216        1656     3533824   82  Linux swap / Solaris
/dev/sda6            1656       30402   230896640   83  Linux

  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              1        1023     7833080    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
```

It will depend on your exact settings, it may not be /dev/sdc1, but something else. 
So make a directory to mount it in and mount

```
sudo mkdir /media/usb
sudo mount /dev/sdc1 /media/usb

```
If it's not /dev/sdc, substitute the last command with the appropriate value.

---

