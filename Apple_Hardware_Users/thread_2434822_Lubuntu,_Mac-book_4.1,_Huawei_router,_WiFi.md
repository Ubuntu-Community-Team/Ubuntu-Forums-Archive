---
title: "Lubuntu, Mac-book 4.1, Huawei router, WiFi"
date: 2020-01-11
forum: Apple Hardware Users
---

### Post by robilio on 2020-01-11
Hello,
I'm successfully installed Lubuntu 19.10 on my Mac-book 4.1 and also wifi was working flawlessly until I tried to use it with a Huawei B535 router... Instead with the previous router (TP-Link Archer D50) the WiFi 2.4 GHz has always worked fine.
With this router my Lubuntu sees the WiFi wlan at 2.4 GHz, seems to connect without problems but actually it doesn't work: internet is down and also the local wlan is down because I can't reach the webpage of the router.
I've run the wireless-info script, the result is here: [https://paste.ubuntu.com/p/Nj4RMbpqCY/](https://paste.ubuntu.com/p/Nj4RMbpqCY/)

Thank you all in advance,
bye R.

---

### Post by jeremy31 on 2020-01-11
Moved to Apple Hardware, try this command in terminal, then reboot
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
That will disable wifi power management

---

### Post by robilio on 2020-01-11
> **jeremy31 said:**
> Moved to Apple Hardware, try this command in terminal, then reboot
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
That will disable wifi power management
This did non work :(
Same as before...

---

### Post by robilio on 2020-01-18
Anybody else?
In the mean time I've "paved and nuked" with a brand new Kubuntu 19.10 and also I did reset to factory settings the Huawei router, but the situation is always the same... :confused::confused::confused:

I keep waiting a kind suggesion ](*,)

Bye,
R.

---

### Post by gsahli on 2020-01-18
A suggestion - check what DNS server your Mac is using. Is it using the IP address of the router? Try adding another DNS like 8.8.8.8.

---

### Post by robilio on 2020-01-19
> **gsahli said:**
> A suggestion - check what DNS server your Mac is using. Is it using the IP address of the router? Try adding another DNS like 8.8.8.8.

OK but.. where should I add the new DNA server? Is there a configuration file?

Thank you! 
Bye, R.

---

### Post by gsahli on 2020-01-19
Try Control Center > Network > DNS tab > add
or
System Settings > Network > Options button > IPv4 settings
(these vary with desktop choice)

---

### Post by robilio on 2020-01-19
Also with the new DNS wifi does not work...
The weird thing is that even ping doesn't work: I can ping only myself!
```
[FONT=monospace][COLOR=#54FF54]**attilio@MacBook41**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ ifconfig  [/COLOR]
ens5: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:1e:c2:15:36:b7  txqueuelen 1000  (Ethernet)
        RX packets 899  bytes 778258 (778.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 966  bytes 139550 (139.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17   

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 714  bytes 56909 (56.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 714  bytes 56909 (56.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wls4: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.8.101  netmask 255.255.255.0  broadcast 192.168.8.255
        inet6 fe80::e867:adb8:df8e:772  prefixlen 64  scopeid 0x20<link>
        ether 00:1e:c2:a4:e1:f1  txqueuelen 1000  (Ethernet)
        RX packets 1462  bytes 760021 (760.0 KB)
        RX errors 0  dropped 4  overruns 0  frame 24215
        TX packets 1764  bytes 281777 (281.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16   

[COLOR=#54FF54]**attilio@MacBook41**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ ping -c 4 192.168.8.1[/COLOR]
PING 192.168.8.1 (192.168.8.1) 56(84) bytes of data.

--- 192.168.8.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3069ms

[COLOR=#54FF54]**attilio@MacBook41**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ ping -c 4 192.168.8.101[/COLOR]
PING 192.168.8.101 (192.168.8.101) 56(84) bytes of data.
64 bytes from 192.168.8.101: icmp_seq=1 ttl=64 time=0.067 ms
64 bytes from 192.168.8.101: icmp_seq=2 ttl=64 time=0.088 ms
64 bytes from 192.168.8.101: icmp_seq=3 ttl=64 time=0.092 ms
64 bytes from 192.168.8.101: icmp_seq=4 ttl=64 time=0.088 ms

--- 192.168.8.101 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3067ms
rtt min/avg/max/mdev = 0.067/0.083/0.092/0.009 ms
[COLOR=#54FF54]**attilio@MacBook41**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ ping -c 4 8.8.8.8[/COLOR]
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3050ms[/FONT]
```

Thanks!
Bye, R.

---

### Post by gsahli on 2020-01-19
What is the IP address of your new router?

---

### Post by robilio on 2020-01-20
> **gsahli said:**
> What is the IP address of your new router?

It's 192.168.8.1, that's one of the addresses I tried to ping in my previous post.

Thank you.
Bye, R.

---

### Post by daniewicz on 2020-01-25
disable IP6-CONNECTIVITY ?

---

### Post by robilio on 2020-01-25
Hello,
I'm back to tell you that googling for my MacBook wifi card/model # I've eventually found the solution to all my problems! :) :) :)
And the main reason was still the driver... I've understood it when (through a command that now I don't remember) I've seen that the active working driver was still "wl" and not "b43".
So, with the help of answer #2 posted by chili555 ([https://askubuntu.com/questions/557348/apple-macbook-air-model-1-1-lubuntu-14-04-64-bit-wifi-broadcom-bcm4321-doesn](https://askubuntu.com/questions/557348/apple-macbook-air-model-1-1-lubuntu-14-04-64-bit-wifi-broadcom-bcm4321-doesn)) and a post by Hadaka ([https://ubuntuforums.org/archive/index.php/t-2327185.html](https://ubuntuforums.org/archive/index.php/t-2327185.html)), I "purged" both wl and b43 driver, re-installed b43 and blacklisted wl:
```
sudo apt update
sudo apt remove --purge bcmwl-kernel-source
sudo apt remove --purge firmware-b43-installer
sudo apt install firmware-b43-installer
sudo -i
echo "blacklist wl"  >>  /etc/modprobe.d/blacklist.conf
exit
```


I've done also this```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```but I'm not sure it was necessary.


With this modifications now the wifi is working perfectly, with both routers.
Thank you all guys!
Linux is always the best community!


Bye, R.

---

