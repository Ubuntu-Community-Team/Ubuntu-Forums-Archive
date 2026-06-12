---
title: "Bluetooth is not working.(Bluetooth 3.o/Asus X44H/Ubuntu 11.10)"
date: 2012-01-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by akpk on 2012-01-06
Bluetooth is not working in my Asus X44H.(It is Bluetooth 3.0-as i read in the user manual)
I am using Ubuntu 11.10.
Please Help.
Thanks.

---

### Post by adrien214 on 2012-01-18
can you tell us the output of the following command in the terminal:

```
sudo rfkill list all
```

---

### Post by bpb101 on 2012-01-18
this i think happens to me, it say bluetooth is on but it not working 
this, although not ideal fixes the problem for me 
it will stop and start bluetooth again...
you must do it every time you start up the pc though.

```
sudo /etc/init.d/bluetooth restart
```

[B]PS. Turning the bluetooth off and on again dosent work you must use this code.
PS This is a temporary fix[/B]

---

### Post by sidd1212 on 2012-01-19
exact same laptop and exact Same problem

 rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by bpb101 on 2012-01-22
the reset although not ideal does work!

---

### Post by sidd1212 on 2012-01-25
> **bpb101 said:**
> the reset although not ideal does work!
sorry does not work .

---

