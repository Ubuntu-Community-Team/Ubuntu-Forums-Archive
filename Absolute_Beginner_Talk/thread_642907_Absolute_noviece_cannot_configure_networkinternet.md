---
title: "Absolute noviece: cannot configure network/internet"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by neatHandwriting on 2007-12-17
Hey good Ubuntu people,

I've recently installed Ubuntu 7.10 on my Sony Vaio PCV RS100 and everything went fine except the network / internet configuration. I've been reading boards (including some topics like [http://ubuntuforums.org/showthread.php?t=276739](http://ubuntuforums.org/showthread.php?t=276739)) on this one but mostly anything I try ends up failing. Could you please give me some pointers?

I've tried the manual wired connection (I don't have wireless) configuration using the System -> Administration -> Network option from the toolbar and tried to connect using every mode listed (Static IP, DHCP, IPv4LL) but neither of them let me ping any address (like 66.102.9.147).

Following the advice on another forum, I also tried to configure the network setup using "sudo pico etc/network/interfaces" and changing the said file to:

```
auto lo
iface lo inet loopback

iface eth0 inet static
address ...
netmask ...
gateway ...

auto eth0
```

I am running a dual-boot with WinXP and have a router. I have some experience with the command line but I don't know much about Linux. Any advice you'd be able to give me would be great!

Thanks very much.
:KS

---

### Post by hyper_ch on 2007-12-17
Ok, start windows, open a terminal there, and type:

```

ipconfig /all

```

And post the output here. That will give basic clues on how your network is setup.

---

### Post by neatHandwriting on 2007-12-17
Hi there, thanks for your reply.
The output is below from Windows:

C:\Documents and Settings\Enrico>ipconfig /all

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : Enrico-Vaio
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : vc.shawcable.net

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : vc.shawcable.net
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-E0-18-EF-BA-E0
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.123.187
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.123.254
        DHCP Server . . . . . . . . . . . : 192.168.123.254
        DNS Servers . . . . . . . . . . . : 64.59.144.90
                                            64.59.144.91
        Lease Obtained. . . . . . . . . . : Monday, December 17, 2007 1:32:33 AM
        Lease Expires . . . . . . . . . . : Monday, January 28, 2008 3:32:33 AM
```

---

### Post by Frunkis on 2007-12-17
The 192.168 IP address indicates 1 of a few different options. I see that you are using DHCP so therefore if is either going to be your router ,if you have one, may not be syncing up with Ubuntu, your modem is in standby, or something is unplugged as most newer modems have an internal DHCP server. Obviously the last two options wouldn't be valid as you are on the internet fine here. I would check your router settings with your network connections in Ubuntu and if it still doesn't work, bypass the router.

---

### Post by neatHandwriting on 2007-12-17
Thanks for your quick reply. I do have a router so I'd like to try what you've suggested:

> check your router settings with your network connections in Ubuntu

Since I'm quite new, where would I start with this?

---

### Post by neatHandwriting on 2007-12-17
Ok, here are some of the things that I've tried so far:

- I changed the network/interfaces file to:

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```

and nothing else and restarted the network. That didn't work.

- I made sure the cable I was using was all right. This wasn't going to be a problem since the computer can connect to the internet with XP but it was worth a check all the same.

- I tried switching the internet cable on the back of the computer to go directly from wall-to-computer, thereby physically bypassing the router. This didn't help - the computer still couldn't connect to the internet in Ubuntu. When I ran the command "sudo /etc/init.d/networking restart" the responses that I got were the same as before: "No DHCPOFFERS received. No working leases in persistent database - sleeping".

- If I tried to connect to my router (with the cables plugged in, of course), I got "cannot establich connection to server at IP.ADRR.XXX.XXX"

So how is it that the internet connection can work in Windows but not in Ubuntu? What more could I try to remedy this?

---

### Post by hyper_ch on 2007-12-18
try to remove the network manager. Sometimes it causes more problems than it helps.

If that still doesn't work, you could assign yourself a static IP (I'd for static anyway).

---

### Post by sisco311 on 2007-12-18
edit you /etc/network/interfaces to:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```and your /etc/resolv.conf to:
```
nameserver 192.168.123.254
```(192.168.123.254 - your routers ip address)

remove your network manager (optional):
```
sudo aptitude remove network-manager network-manager-gnome
```restart your network:
```
/etc/init.d/networking restart
```i hope this will help.

---

### Post by neatHandwriting on 2007-12-18
Thanks, sisco311, I followed your advice. Still no success, though :( I get the same "No DHCPOFFERS received. No working leases in persistent database - sleeping." message when I restart the network.

hyper_ch, I assigned myself a static IP using the following method:
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0
```
but when I restart the network, I get a "SIOCADDRT: No such process Failed to bring up eth0" message.

Curiously, I can always ping 169.254.11.38 but I don't know what this is.
Thank you all so much for your help so far!

---

### Post by x-to-tha-t on 2007-12-18
try typing
```
route
```
you should see a table which reads something like:
```

Destination        Gateway          Genmask         Flags    Metric    Ref    Use    Iface
192.168.123.0    *                    255.255.255.0   U          0           0       0       eth0
default              192.168.123.1  0.0.0.0             UG        0           0       0       eth0

```

Sorry the table looks so crappy.

If either of these lines are missing then you have a configuration problem.

If you can ping an external IP that sounds like a DNS problem. You may have to enter your ISP's DNS settings into /etc/resolv.conf, although this is a last resort.

Something which worked for me is to replace network manager with WiCD. ([http://wicd.sourceforge.net](http://wicd.sourceforge.net)) I don't know if that is only wireless though.

---

### Post by neatHandwriting on 2007-12-19
That was quite helpful - I finally found out that 169.254.11.38 is some default value that pops up when i run
```
ip address show dev eth0
```
This is not the IP that I get from Windows on the same computer, so I don't know what's up.
So far, I've been unable to modify this. I will be reading about IP Routing for now. 

If someone has encountered this kind of situation before, I'd appreciate your advice.

---

