---
title: "Maybe AR5008 (airport extreme) Windows drivers for ndiswrapper on 64 bits :D"
date: 2007-08-01
forum: Apple Intel Users
---

### Post by Azathoth_ on 2007-08-01
Could anyone on a 64 bits system try this on ndiswrapper?
If this works, all ndiswrapper users like me could use a complete 64 bits systems :D

Thanks

[http://www.x-drivers.com/component/option,com_remository/itemid,36/func,fileinfo/id,21895/](http://www.x-drivers.com/component/option,com_remository/itemid,36/func,fileinfo/id,21895/)

---

### Post by cyberdork33 on 2007-08-01
yea there has to be a driver out there. Has anyone looked through Acer's stuff, they used to be the source to get 64-bit Broadcom drivers.

---

### Post by Azathoth_ on 2007-08-02
> **cyberdork33 said:**
> yea there has to be a driver out there. Has anyone looked through Acer's stuff, they used to be the source to get 64-bit Broadcom drivers.

Yes, but... it is a Atheros, not a Broadcom... also i'm going to check it.
I have download a daily build live cd  of Gutsy and now:
We have the lirc_gpio module compile :D :D :D by default in restricted modules and i have tried to use this "64-bits NDIS driver" but does not work for me on the live cd... maybe in a fresh install but i am not going to test it

---

### Post by cyberdork33 on 2007-08-02
> **Azathoth_ said:**
> Yes, but... it is a Atheros, not a Broadcom... also i'm going to check it.

Sorry didn't read your Subject line close enough. Airport Extreme uses both Atheros and Broadcom depending on the machine you have.

---

### Post by Azathoth_ on 2007-08-02
Sorry, i thought that Broadcom was only for airport normal and not for extreme. On my macbook C2D it is a Atheros with the chipset AR5008

---

### Post by cyberdork33 on 2007-08-02
AirPort Card Information:

  Wireless Card Type:    AirPort Extreme  (0x14E4, 0x87)
  Wireless Card Locale:    USA
  Wireless Card Firmware Version:    Broadcom BCM43xx 1.0 (4.80.79.1)
  Current Wireless Network:    AirPort is currently turned off

---

