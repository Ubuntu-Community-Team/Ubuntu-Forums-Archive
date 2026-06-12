---
title: "How to Identify an External USB Drive?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2008-03-30
Complete newbie question here. I have an external drive that isn't auto-mounting when I plug it into the USB port. The external drive is actually a mini-DVD camera, but I don't think that should matter; I simply want to access the files written to the disk. I'll also want to only occasionally mount this drive, so I don't need a permanent mounting option. 

It seems the computer is not recognizing there's even a USB drive attached. From what little I know, when I do lsusb before and after I attach the camera there's no difference in the list returned. 

Any suggestions as to where I can begin? If it helps, the drive/camera is a Sony DCR DVD405. Thank you.

---

### Post by Sleestack on 2008-03-30
OK, a little more information here: "lsusb" is, in fact, returning a listing of the device. The initial problem was setting up the camera itself to signal the computer. Here's the listing:

Bus 001 Device 014: ID 054c:00c1 Sony Corp. 

Now...any advice as to how I can temporarily mount this drive, or where I can get an example, or a tutorial? I've done some searches for generic examples but haven't been to successful.

---

### Post by prshah on 2008-03-30
> **Sleestack said:**
> OK, a little more information here: "lsusb" is, in fact, returning a listing of the device. 

Your dmesg will contain details on which device has been attached to your camera; plug it in, enable drive mode (or whatever) on the camera, then ```
dmesg | tail -10
``` will give you the info; maybe something like /dev/sdd1, etc.

---

### Post by Sleestack on 2008-03-30
OK, I found this: 

[86478.700000] usb 1-7: new high speed USB device using ehci_hcd and address 15

And when I turned off the camera, that listing disappeared, and I got this: 

[86560.800000] usb 1-7: USB disconnect, address 15

Does that give me enough information to mount the device?

---

### Post by Sleestack on 2008-03-30
~bump~

---

### Post by mgmiller on 2008-03-30
First, you need to figure out where it is being seen in /dev
so run the command:
```
sudo fdisk -l
```

and look for the entry for the drive.  You may need to unplug and replug the USB cable for it to appear.

Once you know the device name use the pmount command to mount it.

If the fdisk command showed you the drive is /dev/sdg and you want to mount it as "sony_camera"
enter the command:
```
pmount /dev/sdg1 sony_camera
```

Look in /media and you will see a new folder called sony_camera.  

To unmount the drive, use the command pumount with the name of the mount point.
For our example:
```
pumount sony_camera
```
and the entry should disappear from /media

You can now make buttons for your panel to mount and unmount and save a bookmark in nautilus for the mounted location to semi automate the whole thing.

---

### Post by Sleestack on 2008-03-31
Thanks for your reply. I used the "fdisk -l" command but the listing was exactly the same before and after I plugged in the device. It's interesting because the "lsusb" and the "dmesg" listings are definitely returning events when I connect and disconnect the device, I just wish fdisk would return something useful. There's some disconnect there between fdisk and the other commands. Does anyone know where I can go from here?

---

### Post by Sleestack on 2008-03-31
A little more information: 

I found an entry was created in the /dev/disk/by-id directory when the device was connected. When I look at the Properties, it says: 

Link target: /dev/scd1
MIME type: x-special/device-block

I tried the pmount command: 

pmount /dev/scd1 sony_camera
Error: device /dev/scd1 does not exist

So it sees the device, assigns some kind of name to it, but still won't let me mount it.

---

### Post by mgmiller on 2008-04-01
Could you post the output of
```
sudo fdisk -l
```
with the camera attached and turned on to this forum?

---

### Post by Sleestack on 2008-04-01
Thanks for your reply. Here are the results of "sudo fdisk -l" after the device has been plugged-in. 

```
 sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sda2            7834       23845   128616211    7  HPFS/NTFS
/dev/sda3           23846       38295   116069625   83  Linux
/dev/sda4           38296       38913     4964085    5  Extended
/dev/sda5           38296       38913     4964053+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x595ec772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdg: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6adf6ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        4863    39062016    7  HPFS/NTFS

Disk /dev/sdh: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7ff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1        7295    58597056    7  HPFS/NTFS
```

---

### Post by dcstar on 2008-04-01
> **Sleestack said:**
> OK, I found this: 

[86478.700000] usb 1-7: new high speed USB device using ehci_hcd and address 15

And when I turned off the camera, that listing disappeared, and I got this: 

[86560.800000] usb 1-7: USB disconnect, address 15

Does that give me enough information to mount the device?

Post **all** the dmesg information when you plug the drive in, not just what you think is relevant.

---

### Post by mgmiller on 2008-04-02
I just tried my own Canon camera, which works perfectly in Ubuntu, with the fdisk -l command and it does not show up there either, so I guess that is not the way to go.
Hopefully, further investigation of the usb bus will yield useful information.

In your first post, you said:  > The initial problem was setting up the camera itself to signal the computer.

Did you mean that you went into the setup in the camera and tried having it change the way it talks to the computer?  Sometimes there is more than one way these cameras can signal their status to the computer and you need to try alternatives to get it to work.

---

