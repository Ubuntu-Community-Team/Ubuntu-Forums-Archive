---
title: "update from a USB stick?"
date: 2019-08-02
forum: Apple Hardware Users
---

### Post by hmiersch on 2019-08-02
hi.  i have a problem. i have a macbook pro with ubuntu on its internal harddisk. the problem is that when the motherboard died, they gave me a new one, and now it can't boot from that internal harddisk. so i downloaded ubuntu 19.04 and installed it on a USB stick, intending to "Use tools installed by default on the USB stick to repair or fix a broken configuration" as it promises on this page: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)  but where are those tools? the installer only offers me the option to erase the partition and install 19.04 from scratch, which is NOT what i want to do because i think there are some files on that harddisk that i want to rescue. but how do i do that?

---

### Post by slickymaster on 2019-08-02
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by oldfred on 2019-08-02
You should be getting grub menu with UEFI boot and several boot options.
At least one should be try Ubuntu without installing.

Depending on version:
menuentry "Try Ubuntu without installing" {
or this for the Mate flavor, each flavor may be diffrent
menuentry "Try Ubuntu MATE without installing" {

What model Mac?
I do not know Mac, but different models may need different settings.

---

