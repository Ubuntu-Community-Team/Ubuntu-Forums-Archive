---
title: "Request for clarification on instructions to speed web browsing"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2006-11-29
Weiman and Derprankster worked out a way to increase web browsing speed. See [http://www.ubuntuforums.org/showthread.php?t=265955&page=3](http://www.ubuntuforums.org/showthread.php?t=265955&page=3)

Derpranksters prescription is:


1. Disabled IPV6 in Firefox
2. Disabled IPV6 globally
3. Enabled a static IP rather than using DHCP (router is a Linksys) and I am cabled, not wireless)
4. Eliminated a duplicate network profile for my Ethernet card.
5. Moved to OpenDNS rather using my ISP's DNS. Instructions are here.


I've gotten to step 3 and don't know how to entable a static IP rather than using DHCP (I am using a Linksys router that is wired... not wireless). How do I enable static IP??

Then, how to I "move to Open DNS"???

Thanks,
Phil Smith
Duluth, GA

---

### Post by bodhi.zazen on 2006-11-29
> **Phil Smith said:**
> 
3. Enabled a static IP rather than using DHCP (router is a Linksys) and I am cabled, not wireless)

[How to static IP address](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

You will need some information. get it from the command ```
sudo ifconfig
```

> 5. Moved to OpenDNS rather using my ISP's DNS. Instructions are here.

Follow instructions [here](http://www.opendns.com/start/unix.php)

---

### Post by Old Jimma on 2006-11-30
Hi bodi-zazen:

Thanks for your reply. Here is the result of sudo ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:01:02:2C:2B:C9
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1529563 (1.4 MiB)  TX bytes:294001 (287.1 KiB)
          Interrupt:9 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:161660 (157.8 KiB)  TX bytes:161660 (157.8 KiB)


Thanks,
Phil

---

### Post by bodhi.zazen on 2006-11-30
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo gedit /etc/network/interfaces
```

To determine your gateway, ```
sudo netstat -nr
```I think it is 192.168.1.1

Make these changes:> #iface eth0 inet dhcp

# Static IP
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Note, I am not sure of your gateway. It is the IP address of your router...

Save and exit gedit.

Now```
sudo /etc/init.d/networking restart
```

If all goes well you are done....

If not:```
sudo cp /etc/network/interfaces.bak /etc/network/interfaces
sudo /etc/init.d/networking restart
```And post error messages....

---

### Post by Old Jimma on 2006-11-30
bodhi.zazen

Thanks for your reply and advice.

my /etc/network/interfaces file now looks like...

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface

#iface eth0 inet dhcp # commented out

# begin code added

# Static IP
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

# end code added

iface dsl-provider inet ppp
provider dsl-provider
 

Your guess at the gateway IP address was correct.

I did the sudo /etc/init.d/networking restart     and there were no errors. However, web browsing is still rather glacial, slower than dial up.

Is there something else I need to do to speed up web browsing? Is it step 5 in my initial posting?

Thank you for your help,
Phil Smith
Duluth, GA

---

### Post by bodhi.zazen on 2006-11-30
comment out auto eth0

Like this> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
**[color=red]# auto eth0[/color]**

# The primary network interface

#iface eth0 inet dhcp # commented out

# begin code added

# Static IP
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

......




The restart you network:```
/sudo /etc/init.d/networking restart
```

---

### Post by Old Jimma on 2006-11-30
Hi Bodi.zazen:

commenting that line out resulted in firefox not finding any web pages. I removed the comment. Perhaps there is something else described by derpranskter at [http://www.ubuntuforums.org/showthread.php?t=265955](http://www.ubuntuforums.org/showthread.php?t=265955)

I visited the web site in derpranksters instruction #5 at work today, but can't bring the page up now.

Thank you for your help.

Phil Smith
Duluth, GA

---

### Post by bodhi.zazen on 2006-11-30
```
sudo netstat -nr
```To confirm your gateway...

---

### Post by Old Jimma on 2006-12-01
Here is the output:

philipsmith@ubuntuasus:~$ sudo netstat -nr
Password:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0


Thanks,
Phil

---

### Post by Old Jimma on 2006-12-02
Here is my hardware

Toshiba cable modem PCX1100
Linksys cable/dsl router BEFSR81
Asus mother board P4B266

Is there any other info you need?

Thanks,
Phil

---

### Post by bodhi.zazen on 2006-12-03
I am sorry I could find no further information.

Your hardware is listed as supported by Linux....

Perhaps contact Toshiba ? Linux driver ?

---

