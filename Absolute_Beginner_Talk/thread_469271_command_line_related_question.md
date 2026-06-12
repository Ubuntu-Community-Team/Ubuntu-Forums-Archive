---
title: "command line related question"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-09
I am setting up a LAMP server. I am following [this]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3") guide.
I just finished typing in:
> 5 Configure The Network

Because the Ubuntu installer has configured our system to get its network settings via DHCP, we have to change that now because a server should have a static IP address. Edit /etc/network/interfaces and adjust it to your needs (in this example setup I will use the IP address 192.168.0.100):

vi /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
How do I save it?

---

### Post by taurus on 2007-06-09
Press Esc then :wq!

And if you get an error message that you are not root, then run it with sudo.

```
sudo vi /etc/network/interfaces
```

---

### Post by Kobalt on 2007-06-09
Just press this to save & quit > :wq!

---

### Post by ggaaron on 2007-06-09
> **Kobalt said:**
> Just press this to save & quit

In vim?

Edit: Ups, your :wq was displayed as an image, I don't know why, sorry.

---

### Post by tdrusk on 2007-06-09
Thank you both. :)

---

