---
title: "Successful so far... almost. (networking problem)"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Paige on 2005-12-30
I installed Ubuntu today, and everything seems to work all right.
Almost that is. 

I can't connect to the internet.

I connect (via cable on an ethernet card) through a D-link Dl-542 router.
Router and ADSL modem both work fine, I have no problems connecting on my XP-macines. 

My Ubuntu 'puter can communicate with the router, but not access the internet.

Ping is OK
IP-adress is OK

So... What do I try next?

Please keep answers simple as I am a complete Linux newbie, though experienced in networking in Windows.

---

### Post by thekiller on 2005-12-30
If ping is working, then it means you are connected.

---

### Post by lleb on 2005-12-30
ok what can you ping?  can you ping the router, but not the internet?

---

### Post by Paige on 2005-12-30
I'm connected to the router all right, as I said in my first post.
I can ping the router, but not the internet.

---

### Post by Lambert on 2005-12-30
post the output of this command

```
route -n
```

---

### Post by Paige on 2005-12-30
[QUOTE=Lambert]post the output of this command

```
route -n
```[/QUOTE]

Just a sec!

I wonder if this:
[http://ubuntuforums.org/showthread.php?t=109451&page=2](http://ubuntuforums.org/showthread.php?t=109451&page=2)
might be the right solution, but where do i fix it?

---

### Post by Paige on 2005-12-30
Kernel IP routing table
Destination 192.168.0.0
Gateway 0.0.0.0
Genmask 255.255.255.0
Flags U
Metric 0
Ref 0
Use 0
Iface eth2

Destination 192.168.0.0
Gateway 0.0.0.0
Genmask 255.255.255.0
Flags U
Metric 0
Ref 0
Use 0
Iface eth0

Destination 0.0.0.0
Gateway 192.168.0.1
Genmask 0.0.0.0
Flags Ug
Metric 0
Ref 0
Use 0
Iface eth0

---

### Post by richard willacy on 2005-12-30
paige how did you get out to the net can you please tell me thanks

---

### Post by Paige on 2005-12-30
Keep reading this thread, Richard, and you'll see when I'm out there. ;)

---

### Post by lleb on 2005-12-30
[QUOTE=Paige]Kernel IP routing table
Destination 192.168.0.0
**Gateway 0.0.0.0**
Genmask 255.255.255.0[/QUOTE]


ok, that tells me right there you are not pulling a proper DHCP if you are running under dynamic, or you do not have your static configured properly under /etc/network/interfaces

assuming you are on 192.168.0.x and 0.1 is your router, then you can check your /etc/network/interfaces file and make it look something like the following:

```
cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

that will set you up on a static IP of 192.168.0.100 with 192.168.0.1 as the gateway (your router) and should get you up and running on the web.

if not, then you can just add a # in front of everything from iface eth0 inet static down and remove the # in front of the iface eth0 inet dhcp and then issue the following command.    *note*  you will need to issue this command after you make and save the changes to the above file*

```
/etc/init.d/network restart
```

that will completly restart your network and will then assign the static IP to your NIC eth0, you may have to make that eth2, what other network cards do you have installed on this system?

---

### Post by stream303 on 2006-01-25
> I can't connect to the internet.

I connect (via cable on an ethernet card) through a D-link Dl-542 router.
Router and ADSL modem both work fine, I have no problems connecting on my XP-macines. 

My Ubuntu 'puter can communicate with the router, but not access the internet.

Ping is OK
IP-adress is OK

So... What do I try next?


If you look at your **/etc/resolv.conf** file, I'll bet that the dns nameserver listed is the one inside your router.  What you want is to substitute your isp's primary (and backup) nameserver, and prevent the dhcp process from overwriting /etc/resolv.conf with the routers server each time it gets a new lease.

If you know your isp's dns nameservers, edit **/etc/dhcp3/dhclient.conf**
(sudo gedit /etc/dhcp3/dhclient.conf)

and just before the "request" line, add the following (using your real isp nameserver addresses)
[B]
prepend domain-name-servers 123.45.678.90, 123.45.678.91;[/B]
(separate multiple adresses with a comma and don't forget the semicolon at the end)

Now to make these changes work you can bring your ethernet interface down and up again from the terminal:

sudo ifdown eth0
sudo ifup eth0

Let's see how this goes...

---

