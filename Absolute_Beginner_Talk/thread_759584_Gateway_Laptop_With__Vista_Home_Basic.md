---
title: "Gateway Laptop With  Vista Home Basic"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by faerydae on 2008-04-19
I am trying to install ubuntu on this laptop for the first time I love it on my Pc so i'de really like to run with the laptop also. The problem i encountered was after the install ubuntu (7.10) starts but goes directly to a black screen & doesn't finish starting..It's a Ati Radeon Btw I'm thinking it's a Card problem but havnt found much pertaining to my card...
anything i can try would be great.I am newish to the linux world so i'm sure it's something simple that i'm just not aware of :confused:

Thanks in advance for any suggestions !

---

### Post by TeoBigusGeekus on 2008-04-19
Boot up in recovery mode with grub and type

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the vesa driver and see what happens...

When you exit the reconfiguration program just type

```
reboot
```

---

