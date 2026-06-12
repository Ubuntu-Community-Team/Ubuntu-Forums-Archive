---
title: "Trying to install Xubuntu on my iMac G3, need some help"
date: 2010-07-03
forum: Apple Hardware Users
---

### Post by Donzieja on 2010-07-03
Hello, everyone. It's great to be back.

Anyway, I have an iMac G3 with the following specifications:

Grape
333mhz G3
160mb ram
6gb hdd
I believe it's REV A.

Anyway (again), I downloaded the alternate ppc xubuntu 6.06 install cd, burned it on a CD-R, and inserted it into the powered off iMac G3. I started the computer, and held down the "c" key, after which it made some cd spinning noises and proceeded to boot into Mac OS 8.6. It just seems to completely ignore the disk. I've tried this with ubuntu and kubuntu (both 6.06) with no results. Can anyone out there help me?

Thanks,

-Don

-Edit-

Come on, 24 views and no replies?

---

### Post by linuxopjemac on 2010-07-04
Maybe you have to boot from open firmware
[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

```
boot cd:,\\:tbxi
```

As a general hint. md5 check the iso you downloaded and burn at low speed.

---

### Post by Donzieja on 2010-07-04
I did the open firmware thing. I got something along the lines of this:

DISC LABEL: cannot read cd:,\\:tbxi

and also this:

BAD READ: CANNOT OPEN DISC

Those aren't exactly what they said. just the majority of it. Help please?

Thanks,

-Don

---

### Post by linuxopjemac on 2010-07-04
are you sure you took a powerpc version of ubuntu ? I would try a netinstall.

see [here]("http://ubuntuforums.org/showthread.php?t=1454430&highlight=lubuntu") for example.

---

### Post by Donzieja on 2010-07-04
> **linuxopjemac said:**
> are you sure you took a powerpc version of ubuntu ?



Yes, I'm sure.

---

### Post by Donzieja on 2010-07-04
i checked the md5 and it was ok, and I burned it at 1x. I did the OF boot cd thing, and it just stayed at the screen after i hit enter, and remained there. so i tried it with the c key, and it still just booted into 8.6. Help?

---

