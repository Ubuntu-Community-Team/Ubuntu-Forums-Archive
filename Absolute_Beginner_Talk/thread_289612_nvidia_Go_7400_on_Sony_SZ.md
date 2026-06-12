---
title: "nvidia Go 7400 on Sony SZ"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by xfly on 2006-10-31
I use Kubuntu 6.10, 2.6.17-10-generic

I installed nvidia drivers on my laptop in such way:

1. sudo apt-get install nvidia-glx
2. sudo nvidia-xconfig
3. X restart

The information about video in xorg.conf:
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Why identifier of my card is "Generic Video Card" not "Nvidia GeForce Go 7400"? How could I test my video to ensure it's work correctly?

---

### Post by qscgz on 2006-10-31
?

[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by louistan3 on 2006-11-01
you could try doing ```
sudo dpkg-reconfigure xserver-xorg
```

but i thnk the identifier does not affect the performance of the card..

hope it helps :D

---

