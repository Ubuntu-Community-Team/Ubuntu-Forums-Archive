---
title: "video card problems"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by rikguenther on 2006-11-13
ok, this may be a really simple solution, but i have a problem.  i have a relativly old computer.  its a dell optiplex something or other with a 500 mhz celeron processor.  it has an intel chipset with a built in 4 mb graphics card thing.  i personally dont like that and would like to use my 32 mb Nvidia Geforce 100/200 graphics card instead.  so i go into the bios and set it up to boot with an alternate graphics card, and sure enough it works... until it gets past the ubuntu boot screen.  right before it gets to the login, it freezes.  

it works fine when i use the default onboard video, but when i try to use my card it freezes.  really annoying because 4mb isnt very much.  im just wondering if its something i can install to make it work or what because i would really like to use the other video card.  btw if you dont know the video card is kinda older, its not anything new.

EDIT:
i am using dapper ubuntu linux btw.

---

### Post by taurus on 2006-11-13
Try to boot into recovery mode from GRUB and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by rikguenther on 2006-11-13
ill try that when i get home thank you

---

### Post by rikguenther on 2006-11-15
> **taurus said:**
> Try to boot into recovery mode from GRUB and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

ok i used that and it worked wonderfully thank you!

---

