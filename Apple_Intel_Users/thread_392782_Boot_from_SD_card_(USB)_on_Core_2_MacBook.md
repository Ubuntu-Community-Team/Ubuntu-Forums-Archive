---
title: "Boot from SD card (USB) on Core 2 MacBook"
date: 2007-03-24
forum: Apple Intel Users
---

### Post by James_M on 2007-03-24
I think the title says it all.  I'm trying to boot from USB on my intel MacBook and well...I can't.  Now I've pretty much got everything done.  Ubuntu is installed to the SD card and I've got it plugged in via a USB card reader, but I just can't boot from it.  I've been holding down the option key and looking for the USB device as a boot disk, but so far I've only got my windows and OS X partitions showing.  What am I doing wrong?  Thanks for any help you can give me.

---

### Post by ronocdh on 2007-04-02
I'm bumping this because I've googled around like hell and can't find an answer. I see a lot of people saying that the Intel Macs can boot from USB, but ironically everyone seems to be trying to boot OS X from pen drives! Oy vey. And, in case anyone's interested, booting OS X from USB means the pen drive must be formatted HFS+.

Any one here have a bit of wisdom for the OP?

---

### Post by pxwpxw on 2007-04-02
For Apple Mac ibook, the way I do it is to 
put  vmlinux and initrd on the local hard disk with the boot loader,

Then use the linux kernel parameter <root=/dev/sdax> the kernel needs to find the usb root partition. i.e. the linux kernel can find your USB device but the boot loader cant. This applies to a USB stick, or an external USB hard disk. For this you need the usb drive device name as seen by linux, for example /dev/sda2.

I have no idea if the same idea applies to intel macs.

---

### Post by jonathanjouty on 2008-02-03
i am just trying to do the same thing.. just not with ubuntu but with backtrack 3

so ive got a pen drive with a MBR configured to boot backtrack linux on a PC but how to get it started on my macbook

i installed rEFIt which lets u choose to boot from the USB but that doesn't seem to work..

now trying to install GRUB or LILO on top of backtrack and then use rEFIt to boot grub which boots backtrack :confused::confused:

its gonna work!! i hope

---

### Post by cyberdork33 on 2008-02-03
> **jonathanjouty said:**
> i am just trying to do the same thing.. just not with ubuntu but with backtrack 3

so ive got a pen drive with a MBR configured to boot backtrack linux on a PC but how to get it started on my macbook

i installed rEFIt which lets u choose to boot from the USB but that doesn't seem to work..

now trying to install GRUB or LILO on top of backtrack and then use rEFIt to boot grub which boots backtrack :confused::confused:

its gonna work!! i hopeSee the FAQ regarding booting off external devices.

---

### Post by GhettoT on 2008-02-07
I too am curious about this subject. Where can I find the FAQ on booting from external devices? I've been looking and can't seem to find it. Also, is a 2GB Sandisk microSD good enough for this?

---

### Post by cyberdork33 on 2008-02-07
> **GhettoT said:**
> I too am curious about this subject. Where can I find the FAQ on booting from external devices? I've been looking and can't seem to find it. Also, is a 2GB Sandisk microSD good enough for this?I was referring to the Apple Intel FAQ that is stickied in this forum.
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

---

