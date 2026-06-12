---
title: "gutsy, wireless on imac 3rd?"
date: 2007-10-31
forum: Apple Intel Users
---

### Post by spigolo on 2007-10-31
hi, the other night i went for a double upgrade (i was stuck to 6.10). everything went smoothly, 3d was perfect (except having to find out what is now called beryl), the mic is working, i even got bluetooth working.

i still have problems with wireless though, as it seems that my wireless is not recognized. i compiled madwifi (0.9.3.3) but
```

$ sudo iwlist ath0 scan
ath0      Interface doesn't support scanning.

```
or also
```

$ iwconfig 
lo        no wireless extensions.
eth0      no wireless extensions.

```
and such.
actually, i couldnt even find exactly if madwifi was the way to go for the wireless i have (imac 20" c2d 2.16 Ghz 3rd gen, the white one) what chipset is in here? 
any idea or tip?

thanks!

---

### Post by cyberdork33 on 2007-10-31
> **spigolo said:**
> hi, the other night i went for a double upgrade (i was stuck to 6.10). everything went smoothly, 3d was perfect (except having to find out what is now called beryl), the mic is working, i even got bluetooth working.

i still have problems with wireless though, as it seems that my wireless is not recognized. i compiled madwifi (0.9.3.3) but
```

$ sudo iwlist ath0 scan
ath0      Interface doesn't support scanning.

```or also
```

$ iwconfig 
lo        no wireless extensions.
eth0      no wireless extensions.

```and such.
actually, i couldnt even find exactly if madwifi was the way to go for the wireless i have (imac 20" c2d 2.16 Ghz 3rd gen, the white one) what chipset is in here? 
any idea or tip?

thanks!

iMacs have Broadcom Wi-Fi, not atheros, Madwifi only works with atheros. You can use [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") which requires a working windows driver. The link is for Feisty, but it should work pretty much the same way in gutsy.

---

