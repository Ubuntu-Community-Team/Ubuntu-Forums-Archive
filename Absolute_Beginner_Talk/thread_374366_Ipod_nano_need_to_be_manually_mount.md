---
title: "Ipod nano need to be manually mount"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by hanexar on 2007-03-02
I've no problems mounting manually my 2nd gen nano after editing the fstab file. The problems is that I can't get my girlfriend to type command line to get his ipod to work. I'd like to know if there's anyway that it could be automount, just as my others usb drives do? I've already check in my disk manager setting if everything was set correctly, and it seems so. 

Right now, when I plug the ipod in the usb port, nothing happens until I mount it manually...

Any ideas?

---

### Post by Paerez on 2007-03-02
Thats weird because my ipod nano mounts just fine.

Plug in the ipod and type "dmesg | tail -n 25" and paste it in here.

---

### Post by hanexar on 2007-03-02
```
[17214847.532000] sdb: Mode Sense: 68 00 00 08
[17214847.532000] sdb: assuming drive cache: write through
[17214847.532000]  sdb: sdb1 sdb2
[17214847.536000] sd 9:0:0:0: Attached scsi removable disk sdb
[17214847.536000] sd 9:0:0:0: Attached scsi generic sg1 type 0
[17215090.876000] usb 7-2: USB disconnect, address 10
[17215094.644000] usb 7-2: new high speed USB device using ehci_hcd and address 11
[17215094.776000] usb 7-2: configuration #1 chosen from 2 choices
[17215094.776000] scsi10 : SCSI emulation for USB Mass Storage devices
[17215094.776000] usb-storage: device found at 11
[17215094.776000] usb-storage: waiting for device to settle before scanning
[17215099.776000] usb-storage: device scan complete
[17215099.776000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17215099.776000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17215099.780000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[17215099.784000] sdb: Write Protect is off
[17215099.784000] sdb: Mode Sense: 68 00 00 08
[17215099.784000] sdb: assuming drive cache: write through
[17215099.784000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[17215099.784000] sdb: Write Protect is off
[17215099.784000] sdb: Mode Sense: 68 00 00 08
[17215099.784000] sdb: assuming drive cache: write through
[17215099.784000]  sdb: sdb1 sdb2
[17215099.788000] sd 10:0:0:0: Attached scsi removable disk sdb
[17215099.788000] sd 10:0:0:0: Attached scsi generic sg1 type 0

```

---

### Post by sda5150 on 2007-03-03
Looks like your iPod is being detected correctly.

There is a couple of things you can do:

1) If you are using gtkpod to transfer stuff to your iPod there is an option uder
<edit><edit preferences> "General" tab called "Handle mounting/unmounting of iPod".
With this ticked, when you open gtkpod your nano will be mounted automatically.

If that doesn't work (for some people it just doesn't work) you can try:

2) When you open Nautilus there will be an icon on the left hand window called "iPod".
When you double click on this it will mount your iPod.

This will prevent you having to break out to a command line to mount the iPod.

---

### Post by hanexar on 2007-03-04
Thx for the reply.

Actually, the ipod doesn't show in nautilus when I plug it, so I can't mount it there either. I'll give a look at gtkpod later this week. Thx anyway, and if you have any others suggestions, feel free to send them in !

---

### Post by jimbopouliot on 2007-03-04
Ubuntu Edgy Eft (6.10) will not automatically mount 2nd generation iPods. It is a known bug: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/66068](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/66068)

The problem has been fixed in the next version of Ubuntu, Feisty Fawn, which will come out in April 2007.

If you can't wait until then, you may want to try the following fix, taken from the link above.

Go here: [http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/](http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/)

Do what the README file says. In my case, dpkg complained about a missing dependency. I installed it (with apt-get), retried to install the .deb packages, and then dpkg worked. You will need to reboot and, afterwards, Edgy Eft should recognize you iPod automatically (it worked for me).

Good luck.

---

### Post by hanexar on 2007-03-05
Thanx! I'll give it a try when I get back home.

---

### Post by mfdc1969 on 2007-03-08
I have a RIO Forge 512 which raely gets auto-mounted - only after I connect the cable and repeatedly power the player on-off a few times. My symptoms are similar as hanexar describes - nautilus doesn't show device but dmesg/lsusb show it being detected.

Is the fix mentioned specific to "iPod" -- will it benefit me?

Thanks

- Michael

---

