---
title: "can't get an wireless IP address"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by scottchin on 2007-02-03
I just installed ubuntu on my dell 9300 laptop and everything works great!

I am trying to get connected to my wireless network but cant seem to get an IP address. I have setup wep and I get a good solid connection but it will not assign me a address. I have 3 other computers on the network and the connect just fine but one doesn't seem to be able to request a dhcp address?

Any suggestions? I have downloaded many of the utilities from the community but can't seem to get the system to respond.

Scooter

---

### Post by %hMa@?b&lt;C on 2007-02-03
what is your wireless card?

---

### Post by Hanzerik on 2007-02-04
You can try setting your IP as static:
/etc/network/interfaces
```

iface wlan0 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid YOURESSD
wireless-keymode restricted
wireless-key xxxxxxxxxxxxxxxx

auto wlan0

```

With the wireless-key, I had to remove the s: that the network setup tool put there to get my key accepted.
wireless-keymode may not be needed, depends on your router/wireless config.
And depending on your router, you may need to edit the IP to match what your network is setup for. And instead of getting your nameservers through DHCP, you should be able to add the LAN side IP of your router as the name server.

/etc/resolv.conf
```

nameserver 192.168.1.1

```

I have a Dell Inspiron 1705, with the Broadcom 1390 WLAN Mini-PCI card. Do you have to use ndiswrapper with your wireless card? Mine does not have native Linux drivers so I have to use ndiswrapper and a windows driver inf file to get this card to work. I don't use Ubuntu, but I do use Debian Etch which uses the same config files as Ubuntu. 

Oh, and if you do have this type of card and use a SMP (686) kernel and ndiswrapper, you may have issues with irq conflicts. It works great with the standard 486 kernels.

---

