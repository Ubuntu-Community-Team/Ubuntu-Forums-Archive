---
title: "Supergrub question"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-11-23
I have the Grub Loading Stage 1.5, error 17 message and downloaded and burned the 0.9673 version of super grub. My 1st BIOS boot device is my CD drive.  However when I boot up with the iso in the drive I still get the error 17 message.  

I had already tried catlett's July, 2006 advice on how to restore grub and was stopped at the second step by a "File can't be found, error 15"  message.

I have a PaS800d-X motherboard with 2gig hard drive, 512 mg memory, and nothing unusual attached.

Any ideas?

---

### Post by LaRoza on 2007-11-23
Try manually selecting the cd during start up.

---

### Post by njparton on 2007-11-23
You need to extract the iso to a cd rather than just burn it to a cd (or have I misunderstood your post)?

---

### Post by henthorn on 2007-11-23
Thanks for the replies.  

njparton, how do I extract and then burn.  I am brainless when it comes to computers.

---

### Post by kellemes on 2007-11-23
> **henthorn said:**
> Thanks for the replies.  

njparton, how do I extract and then burn.  I am brainless when it comes to computers.

The following link explains how to burn a ISO like you should.. obviously you need to burn SuperGrubDisk and not the Ubuntu-liveCD but the procedure is the same..

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29")

---

### Post by henthorn on 2007-11-23
I am confused.  I thought an iso was an image of the extracted file.  The instructions in the link only say to burn the iso to disk, and say nothing about extracting first.  Can you explain it so I can understand it?

---

### Post by LaRoza on 2007-11-23
> **henthorn said:**
> I am confused.  I thought an iso was an image of the extracted file.  The instructions in the link only say to burn the iso to disk, and say nothing about extracting first.  Can you explain it so I can understand it?

I don't think the poster meant "extract it", but burn as an ISO.

---

### Post by kellemes on 2007-11-23
> **henthorn said:**
> I am confused.  I thought an iso was an image of the extracted file.  The instructions in the link only say to burn the iso to disk, and say nothing about extracting first.  Can you explain it so I can understand it?

Extracting before burning *can* also be an option.. in some cases, it's just more stept to take. So.. not needed.
Just follow the guide to burn the ISO (as an image of a disk).. instead of burning the ISO-file itself.

---

### Post by henthorn on 2007-11-23
I did burn it as an iso but the CD drive just blinks a couple of times and then shuts down and then the Loading Grub stage 1.5, error 17 comes up.

---

### Post by kellemes on 2007-11-23
> **henthorn said:**
> I did burn it as an iso but the CD drive just blinks a couple of times and then shuts down and then the Loading Grub stage 1.5, error 17 comes up.

You probably don't have the cdrom (with SuperGrubDisk) set as first in line to boot.. You need to enter BIOS to change the bootorder of devices.
It is trying to load Grub (error!) where it should load the disk.

---

### Post by henthorn on 2007-11-23
I do have the CD Rom as the first boot device in BIOS, but BIOS seems to ignore itself.

---

### Post by kellemes on 2007-11-23
> **henthorn said:**
> I do have the CD Rom as the first boot device in BIOS, but BIOS seems to ignore itself.

Have you tried disabling all devices from the bootlist except for the diskdrive?

---

### Post by henthorn on 2007-11-23
I do have the CD ROM set as the first boot device in BIOS.  BIOS appears to be ignoring itself. Wish I could delete this duplicate.

---

### Post by henthorn on 2007-11-23
> **kellemes said:**
> Have you tried disabling all devices from the bootlist except for the diskdrive?

No, I will try that.

---

### Post by henthorn on 2007-11-23
Disabled all but the CD ROM but the disk still didn't load.

---

### Post by njparton on 2007-11-23
An ISO file is analagous to a zip file - it's a collection of other files compiled into one. The ISO file itself isn't bootable or readable directly.

Use Nero, Magic ISO or another piece of CD buring software and then select burn image or similar from the menu of your chosen burning software.

---

