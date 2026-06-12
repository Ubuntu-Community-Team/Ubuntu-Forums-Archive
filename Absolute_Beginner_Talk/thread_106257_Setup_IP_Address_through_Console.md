---
title: "Setup IP Address through Console"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by kleptos on 2005-12-20
When it comes to linux, i want to learn it all. So i grabbed Ubunto and love it. So i decided to keep going in and learn more so i downloaded Ubuntu Server. I assume my question is the same for both. I did a search, but probably didnt search for the right words. 

How do i manually setup IP addresses? In the server installs its just the base system and i think its just a console. I dont have anything really installed on it. I am working on a little network and need to setup the IP, how can i do that through the console? I think right now its setup to use DHCP.

---

### Post by lreyes6 on 2005-12-20
you can edit this file

```
 sudo nano /etc/network/interfaces
```

and then enter something like this

```


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

---

### Post by alamba on 2005-12-20
or else:
ifconfig eth0 192.168.0.1

change interface name and IP as appropriate.

Akshay

---

