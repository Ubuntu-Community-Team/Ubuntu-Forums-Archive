---
title: "Dell Vostro- full hardware support"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by badbob100 on 2008-01-29
Does Ubuntu fully work with the Dell Vostro series of laptops? Videocard is the bundled IGP, and will be using wireless.

---

### Post by az on 2008-01-29
Anything Intel should work just fine.

So, if you get intel graphics and intel wireless, you are fine.

---

### Post by badbob100 on 2008-01-29
Looking at the 1500, the 1700 with Nvidia is £70 more expensive, plus vat.

Vostro 1500, Intel® Core&#8482; 2 Duo processor T5270 (1.40 GHz)
2GB RAM, Intel GMA, 160GB HD, 9 cell battery.

£339.58 inc vat and delivery.

---

### Post by Golem XIV on 2008-01-29
There are several issues with the Vostro.  I have a 1400 and these are my experiences:

Intel 965 (X3100) is blacklisted in Compiz, so no desktop effects.  Can be fixed by removing the blacklist or telling Compiz to ignore it, but then it breaks video support.  This in turn can be worked around by not using XV but not all apps will be happy with it.

Also related to the Intel graphics, all 3D games I tried work for a while and then lock up the system.  Additionally, Wine will not run even the simplest DirectX games (Avernum).

Wireless is cranky, I needed to replace Network Manager with wicd, now it works fine with WPA2/AES encryption.

Built-in microphone does not work, couldn't fix it, worked around it by using headphones with mike.

Overall, once you replace the stock network manager with wicd it will be a decent office system, but nothing more.

---

### Post by soapytheclown on 2008-01-30
if you seach the forums with vostro like you should have before this post you'd see that depending on your build there are numerous issues with the vostro range, most of them to do with sound

---

