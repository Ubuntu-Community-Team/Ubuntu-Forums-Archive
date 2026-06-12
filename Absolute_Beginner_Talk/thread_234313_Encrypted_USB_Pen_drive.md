---
title: "Encrypted USB Pen drive"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by brownjl on 2006-08-11
Hi,

I have been experimenting with my usb pen drive trying to create an encrypted partition for a bit of added security.

Here is what I did incase anyone want to try it;

I first install cryptsetup then fdisked my pendrive to create two partitions the first an encrypted one and the second non-encrypted.

Using; 

"sudo luksformat /dev/sda1 -t vfat" I created the encrypted volume.

To mount I use;

cryptsetup -v luksOpen /dev/sda1 usb-crypto
mount /dev/mapper/usb-crypto /media/usb-crypto

and unmount using,

umount /media/usb-crypto
cryptsetup luksClose usb-crypto

Now my problem at the moment I am using kubuntu and I would like an automated way (preferable via gui) which I can use to mount this drive when I plug in and safly unmount...

any ideas?

Cheers

James

---

### Post by The Seeker on 2006-08-11
Give [TrueCrypt](http://www.truecrypt.org/) a try.

---

