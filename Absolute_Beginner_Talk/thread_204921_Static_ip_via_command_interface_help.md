---
title: "Static ip via command interface help"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by cconk01 on 2006-06-27
ok, i have ubuntu with only the command interface and i gave it a static ip using ```
ifconfig eth0 10.0.4.6
``` but now it doesnt have a default gateway and i use open db which is a movie/cd database and uses the internet to get plot titles and stuff. how do i give it a gate way and dns address using the command interface. If thats something dificult then can someone tell me how to tell it to go back to a dynamic ip address, i can just give it an ip address via my router which i guess i should have origionally done...

---

### Post by ubuntuuser on 2006-06-27
Ok, first you use the command ```
ifconfig -a
``` to show all available interfaces. Next, there are two possibilities:

A) You want to use a wired connection. Let's assume that the interface you want to use is eth0. The command to configure it would be like this: ```
sudo ifconfig eth0 10.0.4.6 netmask 255.255.255.0 broadcast 10.0.4.255 up
``` 
B) You want to use a wireless connection. Now let's say that your wireless interface is eth1. You can find out which wireless devices you have with the command ```
iwconfig
```To configure the device, use the following command, and be sure to use your settings: ```
sudo iwconfig eth1 mode managed essid MyHomeNet key 11:22:33:44:55:66:77:88:99:00:11:22:33
```After that, configure the device as mentioned under A), but use eth1 instead of eth0 :-)

After that is done, you need to tell your PC the default gateway. Type ```
sudo route add default gw gateway.IP.here.please
``` Now try and ping your gateway and google. It should work now. To make those changes permanent you need to edit the file /etc/network/interfaces. You need to search for the syntax, I can't help you here. Or you just write the commands you used into a script and execute it when logging in (bad workaround :-)) Good luck.

---

### Post by cconk01 on 2006-06-27
umm... what is the command to just tell it to get its ip address from the dhcp server. i get error ```
SIOCADDRT: File exists
``` after i enter ```
sudo route add default gw 10.0.0.6
```

---

### Post by ubuntuuser on 2006-06-27
That just means that the route is already configured. Type route to see the kernel routing table. To use DHCP, just type ```
sudo ifconfig eth0 up
sudo dhclient eth0
```instead of that long line in A)

---

### Post by cconk01 on 2006-06-27
Thank you. It worked.:D

---

### Post by PixelPixie on 2006-08-09
After trying sudo route add default gw [insert gateway here] I got 

SIOCADDRT: Network is unreachable.

Help?

---

### Post by Jose Catre-Vandis on 2006-08-13
> **ubuntuuser said:**
> Ok, first you use the command ```
ifconfig -a
``` to show all available interfaces. Next, there are two possibilities:

A) You want to use a wired connection. Let's assume that the interface you want to use is eth0. The command to configure it would be like this: ```
sudo ifconfig eth0 10.0.4.6 netmask 255.255.255.0 broadcast 10.0.4.255 up
``` 
B) You want to use a wireless connection. Now let's say that your wireless interface is eth1. You can find out which wireless devices you have with the command ```
iwconfig
```To configure the device, use the following command, and be sure to use your settings: ```
sudo iwconfig eth1 mode managed essid MyHomeNet key 11:22:33:44:55:66:77:88:99:00:11:22:33
```After that, configure the device as mentioned under A), but use eth1 instead of eth0 :-)

After that is done, you need to tell your PC the default gateway. Type ```
sudo route add default gw gateway.IP.here.please
``` Now try and ping your gateway and google. It should work now. To make those changes permanent you need to edit the file /etc/network/interfaces. You need to search for the syntax, I can't help you here. Or you just write the commands you used into a script and execute it when logging in (bad workaround :-)) Good luck.


Many thanks, this was a useful howto :-)

---

