---
title: "ndiswrapper install errors"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by drdubya on 2007-12-16
Hi,

I was trying to install ndiswrapper when i got the following error msg:
/home/dale/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/dale/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/dale/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/name/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/name/ndiswrapper-1.5/driver'
make: *** [all] Error 2

I googled with no luck and there is a similar post on the forums but no answer. 

Any ideas ?

thanks in advance

---

### Post by dstew on 2007-12-16
Apparently you are trying to compile from source. If you really want to do this, we can help you, but if you only want to get a working ndiswrapper program, use Synaptic and install the binary.

---

### Post by drdubya on 2007-12-16
The reason I was installing by souce was I was following the steps in this thread:

[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

I did try installing with synaptic, but I was getting ndiswrapper not found errors

Thanks for looking

---

