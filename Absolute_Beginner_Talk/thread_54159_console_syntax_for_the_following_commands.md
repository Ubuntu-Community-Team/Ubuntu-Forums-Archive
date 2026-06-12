---
title: "console syntax for the following commands"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by s0lid on 2005-08-03
Hi guys! i got this from Ubuntu Starter Guide. My question is how can i do this in CLI mode?

Q: How to activate/deactivate network connections?

   1. Read General Notes
   2. System -> Administration -> Networking
   3. Network settings

Connections Tab -> Select "Ethernet connection" -> Activate/Deactivate

Q: How to configure network connections?

   1. Read General Notes
   2. System -> Administration -> Networking
   3. Network settings

Connections Tab -> Select "Ethernet connection" -> Properties

Connection -> This device is configured (Checked)
Connection Settings -> Configuration: Select "DHCP/Static IP address"

DNS Tab -> DNS Servers -> Add/Delete

Q: How to change computer name?

   1. Read General Notes
   2. System -> Administration -> Networking
   3. Network settings

General Tab -> Host Settings -> Hostname: Specify the computer name

---

### Post by varunus on 2005-08-03
To activate/deactivate eth0:
```

sudo ifconfig eth0 up #to activate
sudo ifconfig eth0 down #to deactivate

```

To use DHCP for eth0:
```

sudo dhclient eth0 #uses DHCP to configure eth0

```

To use static configuration for eth0:
```

sudo ifconfig eth0 down
sudo ifconfig eth0 (IP Address here) netmask (subnet mask here) up
sudo route add default gw (IP Address of gateway here)

```
For example:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.99.14 netmask 255.255.255.0 up
sudo route add default gw 192.168.99.254
```

To change DNS servers:```

sudo nano /etc/resolv.conf
#change contents of file to following:
nameserver (IP address of primary nameserver)
nameserver (IP address of secondary nameserver, optional)
search (search domain, if any)
```


To change hostname:
```

sudo hostname (newhostname)
sudo nano /etc/hostname
#change hostname contents to new hostname

```

---

### Post by s0lid on 2005-08-03
> 
To use static configuration for eth0:
```

sudo ifconfig eth0 down
sudo ifconfig eth0 (IP Address here) netmask (subnet mask here) up
sudo route add default gw (IP Address of gateway here)

```
For example:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.99.14 netmask 255.255.255.0 up
sudo route add default gw 192.168.99.254
```


but you will need to do this everytime you restarted your PC? is there an automated method to input this ip in /etc/network/interfaces?

---

### Post by az on 2005-08-04
sudo apt-get install etherconf
sudo dpkg-reconfigure etherconf

---

