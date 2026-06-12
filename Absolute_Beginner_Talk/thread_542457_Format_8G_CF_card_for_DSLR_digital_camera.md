---
title: "Format 8G CF card for DSLR digital camera"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by dilizent on 2007-09-04
Feisty, kubuntu.

Sandisk Extreme IV 8G currently always viewed as 512MB by linux. Sandisk usb card reader, Imagemate sddr-92. The card is always recognized by udev and konqueror is started. Actually I think I killed it, the card is not mounting.

The camera can use more than 512MB, but linux will have io errors on copying them. Konqueror may show filesizes greater than 0, but the last file a 512MB will be a truncated size and above that they may real filesize but cp and dd will fail with io error on copy.

I tried msformat, parted, fdisk, cfdisk. fdisk and cfdisk always say 512MB size instead of 8G.

I tried writing zeroes with dd to start over. Now all I can do is see 512MB size and make a 512MB partition. Or I can format the card in camera, but linux will only see 512MB. Linux at first would show 8G in mount via "df", but I couldn't use above 512MB.

---

### Post by Golyadkin on 2007-09-12
It will be quite a bit of work, but maybe you can format the disk in a virtual machine that runs Windows ? (or easier, if you maybe have a Windows machine you can use to format it)

---

### Post by dilizent on 2007-09-12
umount /dev/sdb1

parted -i /dev/sdb rm 1 mklabel msdos mkpart primary 32.5kB 8192MB \
 name 1 SAN8G mkfs 1 fat32 print

...but name 1 SAN8G does not do anything. That's OK.

Immediately udev mounts and starts konqueror and the kde wizard.

Now if for some reason linux cannot see files above 512MB I would suspect the card reader. It's sandisk and not that old though.

And I've heard it's best to format in linux because then linux will be able to read the card after the camera uses it.

---

