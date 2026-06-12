---
title: "[SOLVED] usb flash plus mp3 player -- how to make it work"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Anilael on 2008-01-02
I am trying to put some songs on a usb flash which is also an mp3 player. 
It doesn't have any meaningful name on it other than samsung flash.
I can see it in gnome --> Places-->computer but double-clicking it yields
> 
Unable to mount media
there is probably no media in the drive


I unplugged and then plugged it again and run > dmesg | tail
this is what I got:

> 
[343992.191855] sd 16:0:0:0: [sdi] Assuming drive cache: write through
[343992.191859]  sdi:
[343992.198875] sd 16:0:0:0: [sdi] Attached SCSI removable disk
[343992.198937] sd 16:0:0:0: Attached scsi generic sg9 type 0
[348217.690011] usb 8-3.4: USB disconnect, address 13
[348225.870616] usb 8-3.4: new high speed USB device using ehci_hcd and address 14
[348225.963704] usb 8-3.4: configuration #1 chosen from 1 choice
[348225.964093] scsi17 : SCSI emulation for USB Mass Storage devices
[348225.964152] usb-storage: device found at 14
[348225.964155] usb-storage: waiting for device to settle before scanning


I tried mounting it from the command line:
> sudo mount -t vfat /dev/sg9 /media/flash_dir
it returned:
> mount: /dev/sg9 is not a block device

How can I mount it, please?

---

### Post by mmb1 on 2008-01-02
i'm no good with command line input and output, but you might want to check that you have both the "usbutils" and "usbmount" packages installed.

---

### Post by Anilael on 2008-01-02
Thanks for the quick answer.
I didn't have usbmount, I installed it but the problem still exists.

---

### Post by mmb1 on 2008-01-02
No problem, I noticed in your profile bar, it says you're using 5.10, you might want to consider upgrading to gutsy, it could solve your problem.

---

### Post by Anilael on 2008-01-02
I'm actually using gutsy, profile mistake.
Is there any way to launch from gnome with super user privilages?
How can mount the device from the command line, it there is not such a way.

---

### Post by Anilael on 2008-01-03
I finally got how to do it.
I found by > cat /proc/partitions the device name by plugging and unplugging it.
I then used > sudo mount /dev/sde ~/Desktop/flash to mount it and everything is working.
/dev/sde is for the sake of the example of course.

---

### Post by mmb1 on 2008-01-03
Glad you figured it out, no thanks to me, haha! :)

Best of luck

---

