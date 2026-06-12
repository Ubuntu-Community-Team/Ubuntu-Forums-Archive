---
title: "Apple USB Ethernet Adapter"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by donpaco69 on 2008-05-20
i've bought the apple usb ethernet adapter for my macbook air, but it's not recognized on hardy. it seems there is a patch on asix kernel module to make it work, but i don't know how to rebuild just that module and/or make a deb package.

For the moment i've downloaded through apt-get the kernel source 2.6.24.tar.gz, extracted it, then modified asix.c as described on [http://marc.info/?l=linux-usb&m=121080766320582&w=4](http://marc.info/?l=linux-usb&m=121080766320582&w=4)
and i ran fakeroot etc, i've got a linux-image....deb file installed but when i boot it it fails, so  i think it will be easier to just recompile the module on my actual kernel which is 2.6.24-17-generic

ideas/suggestions?

---

### Post by cyberdork33 on 2008-05-20
I will look at it tonight sometime. If you have a patch (or instructions for patching) then it would be most helpful to post it.

probably a bad config on your kernel. I would start from the ubuntu kernel source too.

---

### Post by donpaco69 on 2008-05-20
yes i've the patch here to the asix.c file:

```
diff -puN drivers/net/usb/asix.c~net-usb-add-support-for-apple-usb-ethernet-adapter drivers/net/usb/asix.c
--- a/drivers/net/usb/asix.c~net-usb-add-support-for-apple-usb-ethernet-adapter
+++ a/drivers/net/usb/asix.c
@@ -1440,6 +1440,10 @@ static const struct usb_device_id        produc
        // Belkin F5D5055
        USB_DEVICE(0x050d, 0x5055),
        .driver_info = (unsigned long) &ax88178_info,
+}, {
+       // Apple USB Ethernet Adapter
+       USB_DEVICE(0x05ac, 0x1402),
+       .driver_info = (unsigned long) &ax88772_info,
 },
        { },            // END
 };
```

so in facts it's not really a bug but a missing feature as the device is "brand new".

the best solution would be to just add the module with a deb package, but as i don't know how to do it :s

the recompiling-all-the-kernel solution is also possible but i don't have a correct .config file to have a bootable kernel :(

---

### Post by cyberdork33 on 2008-05-20
> **donpaco69 said:**
> it's not really a bug but a missing feature as the device is "brand new".
If it doesn't work, and you expected it to (especially if there is already a way to fix it) then that is a bug :) This is probably just being implemented in a newer version of the Linux kernel that is not in Ubuntu yet.

---

### Post by donpaco69 on 2008-05-20
so i'll have to wait 5 months to have a chance tu surf ethernet :'(

bad news for me :)

---

### Post by kosumi68 on 2008-06-01
I had the same problem, so I created a patch for download at [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/). No need to compile anything if you dont want to. The module is called patasix, and requires usbnet to be loaded first.

Basically, since asix is part of the kernel, compiling it seems a bit harder than the ubuntu modules. Thus, I moved the necessary files into a separate directory (patasix), renamed the module and compiled as a separate module. Works for me. :-)

---

### Post by edsinger on 2008-12-16
Hello. Is it still possible to get this module? The link is dead:

[http://web.comhem.se/rydberg/Bits/patasix19.zip](http://web.comhem.se/rydberg/Bits/patasix19.zip)

Thanks.

---

### Post by cyberdork33 on 2008-12-17
> **edsinger said:**
> Hello. Is it still possible to get this module? The link is dead:

[http://web.comhem.se/rydberg/Bits/patasix19.zip](http://web.comhem.se/rydberg/Bits/patasix19.zip)

Thanks.
I believe this was patched into the Kernel already:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/232200](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/232200)

---

### Post by Macchi on 2009-08-02
For the record: I can report that the Apple USB Ethernet Adapter works nicely with Ubuntu and the network manager!

(This is a late report but can be good for anyone interested in that particular piece of hardware. The adapter is handy to create test or emergency systems with multiple network interfaces on a standard laptop)

---

### Post by ubu-for on 2009-10-15
> **Macchi said:**
> For the record: I can report that the Apple USB Ethernet Adapter works nicely with Ubuntu and the network manager!
Absolutely right. Thank you for the post!

---

