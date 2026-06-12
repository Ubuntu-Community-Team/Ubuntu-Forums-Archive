---
title: "Kodak USB picture card reader is not reconized?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-09-28
I suppose that when I plug a usb picture card reader to my pc.
A device icon automatically appears on your desktop and Ubuntu pops up a window asking ifou wnat to view the photos from you camera.
But this doesn't happen to me. In fact nothing happens.

Also when I open F-Spot and try import button and its import/select folders "no cameras detected" icon is not highligted.

I have no clue what to do. Can anyone help?

---

### Post by bodhi.zazen on 2006-09-28
Plug in your card.

Open a terminal. Post the output of this command:```
sudo fdisk -l
```
Note that is a small "L" and and not the number 1.

---

### Post by i-m-p on 2006-09-28
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    c  W95 FAT32 (LBA)
/dev/hda2            4866        9543    37576035   83  Linux
/dev/hda3            9544        9729     1494045    5  Extended
/dev/hda5            9637        9729      746991   82  Linux swap / Solaris
/dev/hda6            9544        9636      746959+  82  Linux swap / Solaris

Partition table entries are not in disk order

This is all what it says. Thank you for your help

---

### Post by bodhi.zazen on 2006-09-28
You would need to contact Kodak and see if they make a Linux driver then.

You could try directly connecting your camera, via a usb port, this is what I have done.

---

### Post by i-m-p on 2006-09-28
I did a littl research on kodak usb driver for linux and it seems they don't have it.
[http://lists.freestandards.org/pipermail/printing-user-general/2006/007553.html](http://lists.freestandards.org/pipermail/printing-user-general/2006/007553.html)

It should work without a kodak driver. I might be wrong though.

I might have to make another thread.

Thanks anyway.

---

