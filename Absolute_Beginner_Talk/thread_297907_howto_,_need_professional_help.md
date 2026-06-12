---
title: "howto , need professional help"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by kornoholio on 2006-11-11
i need to change my mac address everytime i run my linux , how can i make a script containing the macaddress i wanna use  that execute on startup ?

---

### Post by taurus on 2006-11-11
Why do you need to change your mac address every time you boot your machine?  Are you changing your ethernet card before you boot your machine or something?

---

### Post by kornoholio on 2006-11-11
no taurus im not , i just need to change my mac address when ever i login to ubuntu for security reasons , is there any way to write a bash script or somethin n make it run at startup?

---

### Post by digby on 2006-11-11
Unless I'm mistaken, the MAC address is something built into the hardware... even if you try to change what is reported via software, it's still sent as a part of every packet you transmit.  

You'll have to find another way to dodge the feds/RIAA/space aliens.

---

### Post by cwaldbieser on 2006-11-12
> **kornoholio said:**
> i need to change my mac address everytime i run my linux , how can i make a script containing the macaddress i wanna use  that execute on startup ?

Do you already know how to change your MAC address manually?  Some cards let you do this using ifconfig.

Do you know about Sys V init scripts (e.g. /etc/init.d)?

Traditionally, you might create a script for the end of the boot up sequence called rc.local and run your custom boot up scripts from there.

---

### Post by loclei on 2006-11-12
to change your mac at bootup you have to 
```

sudo gedit /etc/network/interfaces

```
and add           hwaddress ether XX:XX:XX:XX:XX:XX 
right after the gateway line
it should look like this:
```

iface eth1 inet static
address ***.***.***.***
netmask ***.***.***.***
gateway ***.***.***.***
hwaddress ether XX:XX:XX:XX:XX:XX

```

---

