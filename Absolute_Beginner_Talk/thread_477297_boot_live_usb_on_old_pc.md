---
title: "boot live usb on old pc"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by heavenhating on 2007-06-18
I have an old PC which doesn't support booting from usb or a zip drive but it does support booting from cdrom and floopy. Somebody told me that I can first boot from a bootable cdrom/floopy and then redirect from that floopy to boot from live usb, can anyone explain(detailed) the way to do this.And I already have a live usb that works on other computers.
Or anyone can tell me link of howto about this.
Sorry if i have repeated a post.

---

### Post by LaRoza on 2007-06-18
I think if you use the Super Grub Disk you'll be able to boot from USB, but I am never tried to boot from USB on an older computer.

For Slax, you can get a disk for booting from USB, it might work with other distro's. [http://www.slax.org](http://www.slax.org)

(It at the end of the download list)

---

### Post by pi3832 on 2007-06-18
:confused: Um, why don't you just boot from the LiveCD and install from the CD?

---

### Post by LaRoza on 2007-06-18
> **pi3832 said:**
> :confused: Um, why don't you just boot from the LiveCD and install from the CD?

The OP wants to boot from a USB, nothing is mentioned about installing.

I use many Live OS without installing, including Slax and Knoppix on a USB drive.

---

### Post by heavenhating on 2007-06-18
I donot want to install anything and also I don't want to use Live cd beacuse I always have one Live usb with me.
It's DSL usb.

---

### Post by LaRoza on 2007-06-18
Did the Super Grub Disk help?

---

### Post by heavenhating on 2007-06-18
> **LaRoza said:**
> Did the Super Grub Disk help?

Actually that pc is at my home so I will try it tonight. If you have other suggestion then do post them also.

---

### Post by pxwpxw on 2007-06-18
I cant find a howto, but in principle:

You have to copy the kernel and intrd from the usb stick system, onto a hard disk partition. Then you should  be able to boot that hd kernel using grub (grub cant boot usb direct on old pc - I had one). However the linux kernel can then find the usb root and carry on to start up.

The trick is to give the kernel args when booting from grub, i.e. root=/dev/sdxx
whatever the usb device name is. So you need to find how to do grub command line kernel args, but supergrub or knoppix may help.

---

### Post by Calash on 2007-06-18
On some of the older IBM systems, if you go into BIOS and set it to boot from Drive 1 when there is no second drive it will look to the USB port for this drive.  USB booting can get a bit tricky with older BIOS versions...some see the drive as a floppy, others as a Hard Disk...some disconnect USB for a moment during booting...can be a pain at times.

---

