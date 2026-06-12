---
title: "Possible to manually mount mp3 player?"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by kinseikun on 2006-01-29
Hello,

I have a Rio Nitrus mp3 player that when plugged in I have no access to. The USB view does say that it is there, but I cannot access it. If possible, can someone tell me how I can mount it as a USB drive so that I can access the mp3s as well as delete and write mp3s back to it? The rioutil program does not work for me (I tried). I am learning about commands, so please try to be specific about mounting the drive. Thank you!

---

### Post by frodon on 2006-01-30
I guess your mp3 player use FAT32 file system but check that to be sure. So when you plugged your mp3 player unmount it : ```
sudo umount PATH_TO_MP3PLAYER_FOLDER
```Then mount it with the good rights : [http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)

---

### Post by kinseikun on 2006-01-31
Uh...what?
I don' t know what it's filesystem is, nor how to find out. When my mp3 player is plugged in it does nothing--it's already unmounted--so I don't know where it's folder is at all. All I know is that I have no access to it, but the Device Manager acknowledges that it exists. Is there a way for me to find its USB path and mount it, and then I will be able to see it? (Similar to mounting a second hard drive). I mounted my second hard drive but only after I figured out where it said it existed.

---

### Post by cwaldbieser on 2006-02-01
[QUOTE=kinseikun]Uh...what?
I don' t know what it's filesystem is, nor how to find out. When my mp3 player is plugged in it does nothing--it's already unmounted--so I don't know where it's folder is at all. All I know is that I have no access to it, but the Device Manager acknowledges that it exists. Is there a way for me to find its USB path and mount it, and then I will be able to see it? (Similar to mounting a second hard drive). I mounted my second hard drive but only after I figured out where it said it existed.[/QUOTE]
Try plugging in the device, then type
```

$ dmesg

```
If the device was assigned a device node, it will be logged there (something like /dev/sdb2, for example).  Then you can try mounting it manually with
```

$ pmount device-name-from-step-above

```

---

### Post by kinseikun on 2006-02-01
It doesn't have an address like that when I did it. It looks like this:
Note: in the USB device manager it said that the mp3 player was in 4-5...
 > 
[4442857.370000] Initializing USB Mass Storage driver...
[4442857.376000] scsi0 : SCSI emulation for USB Mass Storage devices
[4442857.432000] usb-storage: device found at 5
[4442857.432000] usb-storage: waiting for device to settle before scanning
[4442857.432000] usbcore: registered new driver usb-storage
[4442857.432000] USB Mass Storage support registered.
[4442862.432000]   Vendor: Memorex   Model: TD 2C             Rev: 1.04
[4442862.432000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4442862.443000] usb-storage: device scan complete
[4442864.573000] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
[4442864.573000] sda: Write Protect is off
[4442864.573000] sda: Mode Sense: 23 00 00 00
[4442864.573000] sda: assuming drive cache: write through
[4442864.578000] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
[4442864.579000] sda: Write Protect is off
[4442864.579000] sda: Mode Sense: 23 00 00 00
[4442864.579000] sda: assuming drive cache: write through
[4442864.579000]  /dev/scsi/host0/bus0/target0/lun0: p1


However, in the device manager, the Rio has this possible path:

sys/devices/pci0000:00/0000:00:10.3/usb4/4-5

I tried to pmount with this address and it said "Error: could not determine real path of the device: No such file or directory"

---

### Post by griz on 2006-02-02
Ok, not sure if this will work for you, but try typing:
sudo modprobe -r ehci-hcd
in a terminal.  It worked for me on standard USB thumb drives and a Creative Labs Muvo USB mp3 player.

Griz.

---

### Post by cwaldbieser on 2006-02-02
[QUOTE=kinseikun]It doesn't have an address like that when I did it. It looks like this:
Note: in the USB device manager it said that the mp3 player was in 4-5...
 

However, in the device manager, the Rio has this possible path:

sys/devices/pci0000:00/0000:00:10.3/usb4/4-5

I tried to pmount with this address and it said "Error: could not determine real path of the device: No such file or directory"[/QUOTE]

I think this bit is what you want: **SCSI device sda: 501760 512-byte hdwr sectors (257 MB)**.  It probably means your mp3 player is being recognized as /dev/sda or /dev/sda1.  Try typing ```

$ ls -al /dev/sda*

```
both before and after plugging in the device.

---

### Post by steve.horsley on 2006-02-03
Try (in this order):

pmount /dev/sda1
pmount /dev/sda

One of them should work.

---

### Post by kinseikun on 2006-02-04
I tried the pmount, didn't work.
It still said "Error: could not determine real path of the device: No such file or directory".
Same for ls for sda and sda1....-_-
My mp3 player is 1.5 gb, which is all taken up, so I don't know what the 257 mb means.

---

### Post by Toxicity999 on 2006-03-04
Well aware that this is old but thought I could be of some help. The Nitrus doesn't use a typical file system, as such it's not made for 'mass-storage' if you notice the default software (obviously... and sadly just for Windows) needs to be installed to access any of the music, and to store other files you need 'RioTaxi'. Theres a Program for Lin called RioUtil being developed (slightly out of date versio in the Repos.) Personally I couldnt get it to identify and connect to my Nitrus... but it can work with it I guess so you might want to give it a try if you catch this post. (Someone should reeeeeally update the version in the repos.)

---

