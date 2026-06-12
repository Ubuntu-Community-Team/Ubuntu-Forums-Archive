---
title: "Eanabling automatic start of Wireles adapter"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by LAOT on 2008-03-02
Dear all of you

Have installed Ubuntu 7.10 on Compaq NC6000 laptop everything works fine, unless.... The wireless USB adapter, I have to manually configure the device after each reboot.

I use System => Administration => Network to do the configuration. 

Any suggestion?

Looking forward to hearing from you

---

### Post by jan quark on 2008-03-02
hmm please post the interfaces file

```
cat /etc/network/interfaces
```

---

### Post by LAOT on 2008-03-02
Hi 

I guess this....

auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-psk 37dcf9c84a0a27c1707df63ccaf5ce7afa5f16d7131b1b868e94441b22a65b09
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid ZyXEL

auto wlan0

---

### Post by LAOT on 2008-03-04
Just for info 

Did a new install of Ubuntu with the Wireles adapter activated and now its start up each time the PC start.

Thanks for help...... :KS

---

