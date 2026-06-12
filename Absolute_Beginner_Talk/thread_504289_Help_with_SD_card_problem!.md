---
title: "Help with SD card problem!"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ZeroXR on 2007-07-19
I am puzzled an odd problem here...

I got a Palm Treo 680 with a 2GB SD card. I plugged up the SD card to my laptop's card reader and tried to clear out some junk files, but Ubuntu had said the items were locked and couldn't be deleted. On ejecting the SD card and reinserting it into my Treo... it had an issue where some files corrupted and the SD had to be reformatted. After reformatting the SD card, I tried reinserting to my laptop... The SD card can't be read!

I tried reformatting it again on my Treo and still nothing... I tried one of my miniSD cards with the SD adapter and Ubuntu reads it without an issue. I am confused and a little sad... The miniSD has not been formatted at all, the file system is vFAT (FAT16)

Can anyone help me out? Is this due to the card being formatted by the Palm OS software? What can I do to make the SD card readable again?

---

### Post by macogw on 2007-07-19
Try formatting the SD card from Ubuntu using GParted.

---

### Post by ZeroXR on 2007-07-19
Just installed gparted and it seem to have removed any traces of a file system, but on reinserting to the phone... it says otherwise.

Tried reformatting the card with the phone and it still won't read it in Ubuntu.

On gparted's analysis, there's a warning message of:

 "Warning: open /dev/mmcblk0p1p1:No such file or directory"

I'm just stumped here. Anyone know by chance?

---

### Post by ZeroXR on 2007-07-19
If this is the wrong place to have this questions, mods, please feel free to move this post!

Anyone from the daytime side who may have insight?

---

### Post by ZeroXR on 2007-07-21
Turns out the seller of my Treo 680 was a scammer trying to get his full price of $200 for his phone and threw in a corrupted 2GB SD card to jack up the price... Worst part is... It may actually be a corrupted 2GB mmc card according to cfdisk and fdisk in Terminal.

---

### Post by chudder on 2007-07-31
I had similar problem in Dapper, a USB card reader could read it but even then, Ubuntu showed only half the capacity that it had.  I couldn't solve that until I upgraded to Feisty.  I still can't get the card to be read in the built in reader but the capacity is all there in the USB card reader.

---

### Post by chaumurky on 2007-09-04
My card gets set to /dev/mmcblk0 - the first partition being /dev/mmcblk0p1. Gparted adds an extra "p1" to the device for some reason and then can't find it (duh). Qtparted doesn't see the device at all... go figure...

```
sudo mkdosfs -F 16 /dev/mmcblk0p1
```got me out of trouble

gotta love the terminal :)

---

