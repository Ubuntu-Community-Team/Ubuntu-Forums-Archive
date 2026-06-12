---
title: "try again - MacBuntu"
date: 2008-08-28
forum: Apple Hardware Users
---

### Post by freakalad on 2008-08-28
howdy folks,

been pretty-much a year since I last checked in.
by my last reckoning, these where still too many significant driver issues so completely scratch my macbook pro (santa rosa?) to run ubuntu dedicated, as i wanted to.(multi-touchpad, wifi, etc)

rtfm! flames aside, has the issues been addressed satisfactory? 
i'd really like to make the move across (maybe keeping a sliver of os/x for firmware/recovery purposes); maybe with the os/x partition runnable in a vm (vmware, virtualbox, qemu? any suggestions?)

ideally some how-to or wiki may help

btw. saw this pretty 'skin': [http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

---

### Post by freakalad on 2008-08-28
ps. i AM trfm'ing the wiki & sticky stread. just enquiring re last missing drivers & pieces

---

### Post by hanzomon4 on 2008-08-28
wifi=ath9k multi-touch pad? You bought this a year ago? Don't think it's a multi touch pad, could be wrong.

---

### Post by kosumi68 on 2008-08-28
The Santa Rosa touchpad is a Geyser model, multi-finger actions are supported out-of-the-box. I believe everything you need is right here:

[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

---

### Post by cyberdork33 on 2008-08-28
> **kosumi68 said:**
> The Santa Rosa touchpad is a Geyser model, multi-finger actions are supported out-of-the-box. I believe everything you need is right here:

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
The multi touch touchpads are only included on the Penryn MacBook Pro (MacBookPro4,1) and MacBook Air that I know of. "Santa  Rosa" usually refers to the 3rd generation MacBook Pro (MacBookPro3,1) that does not have multitouch (and yes, the Penryn MacBook Pros have Santa Rosa chipsets in them too).

[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

@OP: Can you please determine what version MacBook Pro you have? See the "Before you post..." link in my signature for more info.

---

### Post by cyberdork33 on 2008-08-28
> **kosumi68 said:**
> The Santa Rosa touchpad is a Geyser model, multi-finger actions are supported out-of-the-box. I believe everything you need is right here:

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
The multi touch touchpads are only included on the Penryn MacBook Pro (MacBookPro4,1) and MacBook Air that I know of. "Santa  Rosa" usually refers to the 3rd generation MacBook Pro (MacBookPro3,1) that does not have multitouch.

[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

@OP: Can you please determine what version MacBook Pro you have? See the "Before you post..." link in my signature for more info.

P.S. using that term for reading documentation may get you a warning from mods (even the way you are using it for yourself). I would change your wording.

---

### Post by kosumi68 on 2008-08-28
> **cyberdork33 said:**
> The multi touch touchpads are only included on the Penryn MacBook Pro (MacBookPro4,1) and MacBook Air that I know of. 


The mentioned models use the BCM5974 Wellspring devices. I was under the impression that the Macbook Pro 3,1 Santa Rosa (trackpad usb id 0x021a, 0x021b, 0x021c) use the Geyser4 device, which also supports multi-finger actions together with the appletouch driver. I dont have this machine to test, but the code is definitely there in the driver. Am I wrong?

EDIT: My bad - I linked to the wrong santa rosa page. It should be [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa), I guess this was the reason for the confusion.

---

### Post by cyberdork33 on 2008-08-28
> **kosumi68 said:**
> The mentioned models use the BCM5974 Wellspring devices. I was under the impression that the Macbook Pro 3,1 Santa Rosa (trackpad usb id 0x021a, 0x021b, 0x021c) use the Geyser4 device, which also supports multi-finger actions together with the appletouch driver. I dont have this machine to test, but the code is definitely there in the driver. Am I wrong?

EDIT: My bad - I linked to the wrong santa rosa page. It should be [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa), I guess this was the reason for the confusion.
It is interesting if they have the same hardware type because I don't think they started with the multitouch gestures until the penryn MacBook Pro came out. Can anyone confirm that multitouch is enabled on a machine other than the MacBookPro4,1 or MacBookAir1,1 ? In OSX or otherwise?

---

