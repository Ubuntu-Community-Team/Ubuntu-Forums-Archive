---
title: "permanent mtu"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by eiolv on 2007-05-24
For my Internet connection to work properly, I have to change mtu to 1400. To have that be done permanently I have edited /etc/network/interfaces like this: 
```

auto eth0
iface eth0 inet dhcp
mtu 1400

```
But running ifconfig after boot reveals that mut is set to 1500, so I have to set it manually any way. What have I done wrong? And what is mtu anyway? Is there any advantage using a big or a small number, should I test with others and it might give me a bether Internet?

---

### Post by dreadlord_chris on 2007-05-24
> **eiolv said:**
> For my Internet connection to work properly, I have to change mtu to 1400. To have that be done permanently I have edited /etc/network/interfaces like this: 
```

auto eth0
iface eth0 inet dhcp
mtu 1400

```
But running ifconfig after boot reveals that mut is set to 1500, so I have to set it manually any way. What have I done wrong? And what is mtu anyway? Is there any advantage using a big or a small number, should I test with others and it might give me a bether Internet?

MTU = Maximum Transmission Unit. Basically it defines the maximum size chunk of data your connection can handle without fragmenting the data stream.
[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

Sorry, I don't know why your change isn't holding though.....

---

### Post by eiolv on 2007-05-25
Thanks anyway

---

