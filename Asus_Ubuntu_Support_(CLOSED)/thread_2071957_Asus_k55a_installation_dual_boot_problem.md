---
title: "Asus k55a installation dual boot problem"
date: 2012-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by red111 on 2012-10-16
Hello all, 

I recently attempted to dual boot windows 7 with an old 9.10 ubuntu live usb using install side by side option. the installation seemed to work properly however now i cant boot anything.  The message "reboot and select proper boot device or insert boot media in selected boot device and press a key" appears instead of any kind of boot sequence.

Any help here would be great, particularly with recovering windows. there is also a windows recovery partition that i can't access.  

Thanks

---

### Post by jrog on 2012-10-16
> **red111 said:**
> Hello all, 

I recently attempted to dual boot windows 7 with an old 9.10 ubuntu live usb using install side by side option. the installation seemed to work properly however now i cant boot anything.  The message "reboot and select proper boot device or insert boot media in selected boot device and press a key" appears instead of any kind of boot sequence.

Any help here would be great, particularly with recovering windows. there is also a windows recovery partition that i can't access.  

Thanks
I have an Asus k55a as well. If yours is like mine, then Windows 7 is installed in EFI mode. I'm not sure that Ubuntu 9.10 even supports EFI booting, so I suspect that that is at least part of the problem. You might try performing steps 1 and 4 of the instructions at the top of this link to see if that helps at all: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

