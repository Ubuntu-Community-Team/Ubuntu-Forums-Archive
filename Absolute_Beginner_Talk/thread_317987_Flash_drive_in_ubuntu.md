---
title: "Flash drive in ubuntu"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-13
I have some data that in a flash drive that i want to copy to my ubuntu machine , how do i go about doing this ?

---

### Post by daller on 2006-12-13
Doesn't it work simply plugging it in?

Does it show as a device on the computer? (What is the output from the command: lsusb  ???)

---

### Post by thomasaaron on 2006-12-13
Basically, you should just have to plug it in to a USB port, wait for it to pop up on your screen and then drag anything in it to your desktop.

Of you could go to the terminal manually copy files out of it:

cp /media/usbdisk/filename destination_path

---

### Post by lance_klusener on 2006-12-13
Bus 001 Device 003: ID 0781:5406 SanDisk Corp.
Bus 001 Device 001: ID 0000:0000 

According to me it is detecting the snadisk drive , but how do i go about accesssing it , since i cannot see the flash drive in my computer ( as is the case in windows )

---

### Post by lance_klusener on 2006-12-13
There is no usbdisk in the medis folder , i have tried plugging in the flash drive a couple of times 

:(

---

### Post by thomasaaron on 2006-12-13
try plugging in your usb drive

go to a terminal and type: sudo updatedb

that will take a minute or two to complete.

then type: locate filename
filename is the name of a file you want to retrieve from the usb drive
make sure to include any extensions

this should search your computer for that file and maybe show you the path to it.

then maybe you can use the copy command I mentioned earlier to manually copy the files you need.

---

### Post by thomasaaron on 2006-12-13
if that doesn't work, I'm not sure.
Perhaps you could upload the files to another machine and email them to yourself.


if you can't upload onto a windows computer either, perhaps your flash drive is dead.

---

### Post by lance_klusener on 2006-12-13
No luck with the givne instructions , i should say one thing the machine that i hvae is ubuntu and its running virtually using vmware workstation.

---

### Post by dmartinsca on 2006-12-13
When you plug the drive in, wait a few seconds, then run **dmesg** in a terminal. You should see something like this:
```
[17276898.988000] usb 5-3: new high speed USB device using ehci_hcd and address 6
[17276899.132000] usb 5-3: configuration #1 chosen from 1 choice
[17276899.420000] usbcore: registered new driver libusual
[17276899.468000] SCSI subsystem initialized
[17276899.472000] Initializing USB Mass Storage driver...
[17276899.472000] scsi0 : SCSI emulation for USB Mass Storage devices
[17276899.472000] usbcore: registered new driver usb-storage
[17276899.472000] USB Mass Storage support registered.
[17276899.472000] usb-storage: device found at 6
[17276899.472000] usb-storage: waiting for device to settle before scanning
[17276904.472000] usb-storage: device scan complete
[17276904.472000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 1.04
[17276904.472000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17276905.632000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17276905.632000] sda: Write Protect is off
[17276905.632000] sda: Mode Sense: 23 00 00 00
[17276905.632000] sda: assuming drive cache: write through
[17276905.636000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17276905.636000] sda: Write Protect is off
[17276905.636000] sda: Mode Sense: 23 00 00 00
[17276905.636000] sda: assuming drive cache: write through
[17276905.636000]  sda: sda1
```
The important lines are the last few. They indicate that the device has been assigned to /dev/sda and the partition on it is /dev/sda1.
If the drive isn't recognized like this then i suspect there is a problem somewhere due to vmware. I don't have any experience with vmware so i can't help you out on that one.

---

### Post by lance_klusener on 2006-12-13
No i am not seeing any SDA1 although i see SDA2

---

### Post by K.Mandla on 2006-12-13
> **lance_klusener said:**
> No i am not seeing any SDA1 although i see SDA2
It's funny that your drive doesn't just pop up when you insert it. Make sure sda2 is the USB drive with

```
sudo fdisk -l
```
The size fdisk reports for sda2 should match your flash drive. Now

```
sudo mkdir /media/flashdrive
```
to make a mount location for the drive, then

```
sudo mount /dev/sda2 /media/flashdrive
```
to mount the drive to the file system. 

At this point you should be able to 

```
ls /media/flashdrive
```
and see the files on the drive. If you start Nautilus (or whichever file manager you use) you should be able to navigate to /media/flashdrive and copy the files you want.

---

### Post by Iarwain ben-adar on 2006-12-13
Lance:
i had the same problem,
and what i did (actually i just did nothing),
but try to upgrade your kernel to something 17+

This is what i read around, and now it works.


Iarwain

---

### Post by dmartinsca on 2006-12-13
Ok, so I said I didn't know anything about vmware but I decided to install WindowsXP in a virtual machine this afternoon. Something I've noticed is that usb devices are not automatically taken over by the virtual machine, presumably because they can only be accessed from either the virtual machine or the host OS at one time.

Anyways, a couple of things to check. If you're using VMware server, you can edit hardware that is available in the virtual machine, make sure you have USB devices available. If you don't you can add them, i'm not sure on the parameters you'll need, i'll look in to that in a bit.

If you have USB devices available to the virtual machine, then after you plug in the drive & the ubuntu VM is running, click on the VM menu, go to removable devices, then usb. Choose the one for the drive and it should become available to ubuntu, which will hopefully just open it. You should probably make sure to do the whole 'safely remove device' thing from windows before you do this.

---

