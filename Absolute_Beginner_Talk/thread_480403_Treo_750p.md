---
title: "Treo 750p"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by mcmilner on 2007-06-21
I'm thinking of getting a new smartphone.  Since the few people I know on Linux have Palm TXs, I have been looking at the Treo 750p.  Is Palm better for synching?
I found the instructions for synching the 650.  Are those likely to work for the 750?
Thank you.

---

### Post by wormser on 2007-06-22
I do not think that guide will work.  The [Treo 650]("http://www.engadget.com/2004/10/24/treo-650-is-official/") is a PalmOS device and the [750]("http://www.palm.com/us/products/smartphones/treo750/") is a Windows Mobile (CE) based device.  If I was you I would take a look at Apple's [Iphone]("http://www.apple.com/iphone/") too.  It is being released on the June 29th.

---

### Post by mcmilner on 2007-06-22
I tried to fix this, so there is another post somewhere.  I really meant to say the 755p.

---

### Post by lazyart on 2007-06-22
Don't the Palms come in 'p' and 'w' versions for PalmOS and Windows Mobile?

I had a Dell Axim and sold it for a Palm T|X just because it works better in Linux.  I'd imagine they 755 would sync just as easily by USB.  I use JPilot which apparently is a lot like the Palm software on Windows (I've yet to connect my T|X to a Windows box so I'll take their word on it.

I'd think the guide would work the same way.

---

### Post by panthar on 2007-06-22
I just got a Treo 755p and to make it work, I created the file:

```
/etc/udev/rules.d/10-custom.rules
```

Inside this file, I entered:

```
SUBSYSTEM=="usb", ATTR{idProduct}=="0061", ATTR{idVendor}=="0830", RUN+="/sbin/modprobe visor"
```

This loads up the correct palm module so when the symlink step of udev gets triggered, it links /dev/pilot to the correct node.  I have tested this and the pilot tools work correctly using /dev/pilot (tried pilot-read-todos, etc)

---

### Post by mcmilner on 2007-06-22
Thanks, I'll hang on to the code.

---

### Post by rp3 on 2008-03-02
> **mcmilner said:**
> Thanks, I'll hang on to the code.

Did you ever get this to work?

I just tried and I see the data in dmesg shows this

[http://paste.ubuntu-nl.org/58206/](http://paste.ubuntu-nl.org/58206/)

Doesn't look correct, but gets a bit further, as it's not a visor but....

When i try to setup gpilot, it can't find the device when it asks for a sync button... Just nothing happens no matter what I do???

:confused:

---

### Post by ljoslin on 2008-03-05
> **rp3 said:**
> Did you ever get this to work?

I just tried and I see the data in dmesg shows this

[http://paste.ubuntu-nl.org/58206/](http://paste.ubuntu-nl.org/58206/)

Doesn't look correct, but gets a bit further, as it's not a visor but....

When i try to setup gpilot, it can't find the device when it asks for a sync button... Just nothing happens no matter what I do???

:confused:


I had this working about one month ago, then I'm not sure what changed, but now the phone won't even show up on kern.log or any other when it's plugged into the USB?  Anybody have any ideas?

-=ljoslin=-

---

