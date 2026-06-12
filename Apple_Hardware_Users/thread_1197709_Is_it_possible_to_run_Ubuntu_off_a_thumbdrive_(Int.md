---
title: "Is it possible to run Ubuntu off a thumbdrive? (Intel Macbook)"
date: 2009-06-26
forum: Apple Hardware Users
---

### Post by Spen on 2009-06-26
If so, how would I go about booting Ubuntu off a USB thumb drive on a Macbook?

Thanks

---

### Post by nmaster on 2009-06-26
[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

you can just google ubuntu usb and find lots of info. this is just one link i found in 30 seconds.

---

### Post by Spen on 2009-06-26
Yeah, I have a flashdrive with Linux on it, but my Macbook does not want to boot from it.

---

### Post by Therion on 2009-06-26
Sure it's possible.  

I once ran Ubuntu on a rig I cobbled together from an old soup can, a hair-dryer and a handful of York Peppermint Patty wrappers.

---

### Post by vonlaken on 2009-06-26
if you install ubuntu to a thumbdrive and boot with rEFIt and GRUB2, you can.....
I haven´t managed to have a usb live distro though..............

---

### Post by Spen on 2009-06-26
The harddrive is broke, I was just looking for something to play around with till a new one gets here.

Thanks guys!

---

### Post by Richardcavell on 2009-06-27
For ordinary users, you can't.

For advanced users, it's possible using GRUB2.  Someone ought to create some simple instructions for this (I'll do it myself once I've smoothed out the MacBook Ubuntu installation instructions if no one else does it first).

Richard

---

### Post by hajk on 2009-07-02
Grub-efi excepted (which isn't quite ready for prime time yet), Linux can only be booted from one of the GUID partitions numbered 1..4 or from a CD-ROM. That boot partition need not be large, just enough to hold the contents of the /boot directory (200 MB would be more than enough). Once booted, you can use *any* partition on *any* mounted device, including on your USB thumbdrive, where you would install the Linux / (root) directory and possibly separate /var, /usr or /home sub-directories; as well as a swap partition.

---

### Post by a2z on 2009-07-02
> **Richardcavell said:**
> For ordinary users, you can't.

(I'll do it myself once I've smoothed out the MacBook Ubuntu installation instructions if no one else does it first).

Richard

That would be great! IMHO a stick is at least 3 times better than a disk.
1) no scratches  
2) has a lot more capacity
3) No software to deal with

---

