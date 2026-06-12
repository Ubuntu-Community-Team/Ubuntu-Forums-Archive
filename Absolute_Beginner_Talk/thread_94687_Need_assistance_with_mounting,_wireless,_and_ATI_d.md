---
title: "Need assistance with mounting, wireless, and ATI drivers"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by uPilot on 2005-11-24
I realise I posted this in the wrong forum, so here it is, in the correct forum.

> Hey all!

I installed 5.10 AMD64 on my box last night and the installer failed to load startx. Im assuming this is because I dont have ATI drivers installed for my video card (an X800). Well, I was suggested to use apt get, but I cant because I dont have an internet connection. The installer was unable to configure my wireless card on install.

So, I was told about ndiswrapper for my wireless. So I downloaded it onto my laptop and put it on a USB key. But I have no idea how to mount it.

I have 2 Serial ATA drives, sda and sdb. I also have a floppy and a CD drive. Those are in /media

In /dev I have a directory /usb which contains a single file, usb0 I believe. But I dont know where to go from there.

Any help and suggestions are greatly appreciated

Thanks,
Pilot

---

### Post by endy on 2005-11-24
My USB hard disk shows up as a SCSI device, /dev/sdb to be precise. I'd do a quick 

```
ls /dev/sd*
``` 

and see if anything new appears when the device plugs in. If that fails remove the USB key, wait a few seconds and plug it back in then run the following command and see if it's being detected.

```
dmesg
``` 
For example when I plug in my USB hard disk (which is actually an iRiver MP3 player) I get this output:

```
[4310575.819000] usb 2-6: new high speed USB device using ehci_hcd and address 4[4310576.616000] Initializing USB Mass Storage driver...
[4310576.617000] scsi2 : SCSI emulation for USB Mass Storage devices
[4310576.618000] usb-storage: device found at 4
[4310576.618000] usb-storage: waiting for device to settle before scanning
[4310576.618000] usbcore: registered new driver usb-storage
[4310576.618000] USB Mass Storage support registered.
[4310581.618000]   Vendor: TOSHIBA   Model: MK4004GAH         Rev: JC00
[4310581.618000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4310581.623000] SCSI device **sdb**: 78126048 512-byte hdwr sectors (40001 MB)
[4310581.623000] sdb: assuming drive cache: write through
[4310581.626000] SCSI device **sdb**: 78126048 512-byte hdwr sectors (40001 MB)
[4310581.626000] sdb: assuming drive cache: write through
[4310581.626000]  /dev/scsi/host2/bus0/target0/lun0:
``` 
I've highlighted the important bit. Next you'll need to mount it I assume it's  FAT32 formatted if so the following command should work (you may need to use sudo)

```
mount -t vfat /dev/DEVICE /mnt
``` 
Where "DEVICE" is whatever you found from the dmesg command. Then change directory to /mnt and you should see your files. I hope this helps or at least gets you on the right path :)

---

### Post by uPilot on 2005-11-24
Thanks a bunch! :)

I have 2 Serial ATA drives, which register as sda and sdb.  My USB key registered as sdc.  I assume sdc is the actual USB drive, whereas sdc1 is the partition.  My command was this:

```
sudo mount -t vfat /dev/sdc1 /mnt/sdc
```

Now I can see ndiswrapper:

-rwxr-xr-x [...] ndiswrapper-1.5.tar.gz

I just... dont know how to execute it.  We havent gotten that far in my Linux classes.  I know about permissions, btw.

I'll try to figure it out on my own before comming back here though.

One quick last question:  Do I have to umount the drive before pulling it out?  And is there a way (I guess if I edit fstab) to automount it?

Thanks a bunch, again.

---

### Post by uPilot on 2005-11-28
I was able to unzip ndiswrapper-1.5.tar.gz into a folder, but I dont know where to go from there.  I cant seem to execute anything.

From the text prompt, can I unzip the .tar.gz file?  And once that is done, what do I do to install ndiswrapper?

Thanks

---

### Post by endy on 2005-11-28
I'm not sure myself but the Wiki turned up these results:

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles)

I hope this helps :)

---

### Post by uPilot on 2005-11-28
Umm, is there a "for me" version? :confused:

---

### Post by ssam on 2005-11-28
see if you can follow this one [https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu](https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu)

let us know if you can't manage any steps

---

### Post by uPilot on 2005-11-28
Sorry mate, I read that and was slightly clueless.  I'll keep at it.

---

### Post by uPilot on 2005-11-28
Ok, well I was told I didnt need ndiswrapper.

But I cant seem to configure my wireless card anyways.

I've given installing ATI drivers a try.

Im not entirely sure what Im doing.  I've extracted the x86_64 drivers to a folder and when I try to run ati-installer.sh I get a weird message:

Unrecognized parameter '' tp ati-intaller.sh

Should I build a package or anything?

---

