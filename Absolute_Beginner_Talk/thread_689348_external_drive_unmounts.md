---
title: "external drive unmounts"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Waldo22 on 2008-02-06
I have a Seagate 250 gig usb drive that randomly unmounts.  I was told that I could reformat to a different file system to alleviate this.  Is this correct?  What file sys?  Thanks for your help.

---

### Post by lespaul_rentals on 2008-02-06
This sometimes happens with my external hard drives when I haven't accessed them in a while.  What filesystem is it now?

---

### Post by jan quark on 2008-02-06
plug the drive in and run 
```

sudo fdisk -l 
```

please and post the result

---

### Post by wirawan0 on 2008-02-06
To help diagnose your problem, you can follow these steps.

First, do a clean reboot. Then plug in the hard drive. You will get this kind of message (not exactly equal to this one, since your device will differ; this output is from an external card reader):

```

[1796492.648000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[1796492.824000] usb 2-1: configuration #1 chosen from 1 choice
[1796492.828000] scsi15 : SCSI emulation for USB Mass Storage devices
[1796492.828000] usb-storage: device found at 7
[1796492.828000] usb-storage: waiting for device to settle before scanning
[1796497.828000] usb-storage: device scan complete
[1796497.832000] scsi 15:0:0:0: Direct-Access     IC       USB Storage-CFC  322E PQ: 0 ANSI: 0 CCS
[1796497.832000] scsi 15:0:0:1: Direct-Access     IC       USB Storage-SMC  322E PQ: 0 ANSI: 0 CCS
[1796497.836000] scsi 15:0:0:2: Direct-Access     IC       USB Storage-MMC  322E PQ: 0 ANSI: 0 CCS
[1796497.840000] scsi 15:0:0:3: Direct-Access     IC       USB Storage-MSC  322E PQ: 0 ANSI: 0 CCS

```

Then once it umounts again, invoke `dmesg' again, and copy the output from dmesg starting from that "new full speed USB device using uhci_hcd and address NNN" through the end of dmesg, where it shows a problem. We'll see if there is something strange. 

What kind of hard drive it is (model no, etc.)?

Wirawan

---

### Post by lespaul_rentals on 2008-02-06
> **wirawan0 said:**
> What kind of hard drive it is (model no, etc.)?

This one, I'd assume: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148233](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148233)

---

