---
title: "setting an ethernet connection"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-02-14
I have been aving the same problem in both gusty and hardy alpha 4. When I first install and boot for the first time I enter the information that my isp gave me (ip, subnet, gateway and DNS's) and it all works fine until I reboot. After I reboot in gusty i cannot connect to this network. After I reboot in hard I keep getting an error saying "you do not have permissions to modify the sytem configuration" when i try to activate the wored connection. In both hardy and gusty the eth0 is in the network tools but only shows IPv6, it does not show anything for IPv4. I both hardy and gusty the connection is saved in the "network" thing.

anyhelp would be great.

thanks!

---

### Post by OffAxis on 2008-02-14
The best solution would be  a router that would handle the connection for you.
I don't know why the setting isn't persisting across reboots, but you could try manually editing the  
**/etc/network/interfaces**
file with your settings.

Something like this:
```

iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        gateway 192.168.1.1
```
(changed to your isp appropriate info, of course)

Then a 
```
sudo /etc/init.d/networking restart


```

---

### Post by rockinlinux on 2008-02-15
well I spent all night testing different distros, dreamlinux, Gentoo an Manirva...all of them handle this fine. I decided to switch over to mandriva fulltime....i have been thinking about it for a long time but now i did it. Maybe after Hardy comes out i will switch back but as of now there are to many bugs in hardy and my laptop is not supported good enough in gusty. Hrady looks very promising, i think afer the bugs are gone it will be a great OS and make great for the LTS. Im not one of those people saying im switching to get attention, i have been around linux for a long time and have used many diffferent distros.....i guess i like to change things around :)

---

