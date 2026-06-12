---
title: "Edubuntu Server setup questions"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Honayo on 2007-06-24
I'm not totally new to Ubuntu but have very little knowledge of server apps. I want to install Edubuntu server on one machine and have my kid's computers as thin clients on that network. The thing is that I can't find a post that tells me how to get it done.

Currently, I run a Windows home network and have 5 desktops and one laptop on a wireless setup. Cable modem to Linksys BEFSR41 router and then to an Edimax Wireless 11g Access Point. Most are windows machines but this one is dual boot with XP / Ubuntu 6.06 LTS and another is Kubuntu Feisty only.
I want the server and kid's computers to be totally Edubuntu. Any tips, links, etc would be greatly appreciated.

---

### Post by dbott67 on 2007-07-04
You may already be aware of some or all of this, but it may help future people that find this thread, so I'll try to explain things as thoroughly as possible.

Edubuntu is basically built on 2 things: **Ubuntu** & **LTSP** (Linux Terminal Services Project)

LTSP allows 'thin client' (PCs or network devices with limited CPU power, low RAM & no hard drive) to connect to the server and run a Windowed environment.  The benefit is that the server does all the heavy lifting, and the client is really just for displaying what's happening on the server.

In order to allow the clients to connect, Edubuntu is configured to run it's own DHCP server that provides each client an IP address during boot, as well as where to get the PXE/boot image. From there, the kernel is loaded into memory and the client PC will eventually reach the login screen.

The clients can connect to the server using a number of methods:
- PXE-enabled network cards (they can automatically obtain an IP and download a PXE/boot image from a server)
- Boot disk (floppy, CD-ROM, Hard disk, USB, etc.)
- Fat-client: install an OS (Windows, OSX, Linux, etc.) and then use a secondary application to connect to the server (examples would be: Citrix, NX Machine, Xnest, TSClient, etc.)

If your kid's PC does not have a PXE-enabled NIC, just use [ROM-O-MATIC]("http://rom-o-matic.net/5.4.3/").  I tried it out last week and it works great.

When the thin client connects, the client PC gets essentially gets connected to a secondary installation of Ubuntu (contained in a "[chroot]("http://en.wikipedia.org/wiki/Chroot")" directory).  The server has one install that contains whatever apps & services the server needs and the "clients" get connected to the "chroot" installation, which can contain different applications and different window mangers, if desired (such as Gnome, KDE, etc.).  Whenever you want to work on the "client" installation, you need to type the following command on the server:
```
sudo chroot /opt/ltsp/i386
```Once that's done, you'll be in the "client installation" and you can run commands like apt-get to install new apps, etc.

_**Installing Software for the Clients**_

One caveat is that the "chroot" environment's **sources.list** file does not have the repositories listed, so you need to copy over your sources.list file from the "server" install to the "chroot" install:
```
sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/sources.list
```Then "chroot" over the the client side and run apt-get update:
```
sysadmin@edubuntu:~$ [COLOR=Red]sudo chroot /opt/ltsp/i386/[/COLOR]
Password:
root@edubuntu:/# [COLOR=Red]apt-get update[/COLOR]
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_CA
Get:2 http://ca.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://ca.archive.ubuntu.com feisty/main Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty/multiverse Translation-en_CA
Get:3 http://ca.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://ca.archive.ubuntu.com feisty-updates/main Translation-en_CA
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_CA
Ign http://security.ubuntu.com feisty-security/universe Translation-en_CA
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty-updates/restricted Translation-en_CA
Hit http://ca.archive.ubuntu.com feisty Release
Hit http://ca.archive.ubuntu.com feisty-updates Release
Hit http://ca.archive.ubuntu.com feisty/main Packages
Hit http://security.ubuntu.com feisty-security Release
Hit http://ca.archive.ubuntu.com feisty/restricted Packages
Hit http://ca.archive.ubuntu.com feisty/main Sources
Hit http://ca.archive.ubuntu.com feisty/restricted Sources
Hit http://ca.archive.ubuntu.com feisty/universe Packages
Hit http://ca.archive.ubuntu.com feisty/universe Sources
Hit http://ca.archive.ubuntu.com feisty/multiverse Packages
Hit http://ca.archive.ubuntu.com feisty/multiverse Sources
Hit http://ca.archive.ubuntu.com feisty-updates/main Packages
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://ca.archive.ubuntu.com feisty-updates/main Sources
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 3B in 1s (3B/s)
Reading package lists... Done

```_**Issues:**_

**1. DHCP Servers:** Edubuntu comes with it's own DHCP server, configured as 192.168.0.254 by default.  This DHCP server is different from a typical router DHCP server (such as your Linksys) because it can tell the client where to get the PXE/boot image.  If you run both DHCP servers, you're likely to run into a situation where the client gets an IP from the Edubuntu server at boot time, but when the kernel loads, it gets a different one from the Linksys server (essentially causing the client to 'hang' just after the Edubuntu splash screen).  

My router supports "blacklisting" MAC addresses, so I just added the Edubuntu client PC's MAC address to the router's blacklist and those machines will not use the router for DHCP.

Here's a good primer on DHCP setups for LTSP:
[http://gentoo-wiki.com/LTSP_Server](http://gentoo-wiki.com/LTSP_Server) 
[B]
2. Booting the Client:[/B]  If your network card supports PXE booting (check the BIOS), you can boot from the network and it should find the Edubuntu server and things should just work.  If your NIC does not support PXE-booting, then try ROM-O-MATIC.

Wireless NICs can prove to be troublesome for PXE booting:
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/WirelessLtsp](http://wiki.ltsp.org/twiki/bin/view/Ltsp/WirelessLtsp)

**3. Users:** You'll need to create a 'limited-user' account on the Edubuntu server for your children.

Here's a thread that I posted in recently that provides some insight into my situation:
[http://ubuntuforums.org/showthread.php?p=2945775#post2945775](http://ubuntuforums.org/showthread.php?p=2945775#post2945775)

I hope this is enough to get you started.  Keep posting in this thread if you have any more questions.

-Dave

---

### Post by tr3s on 2007-07-06
hi dbott67,

i already copied the sources.list into the chroot but when i do a ```
apt-get update
``` in chroot, i always get "could not resolve archive.ubuntu.com" error.

am i missing something?

tnx in advance

---

### Post by dbott67 on 2007-07-06
You could be having name resolution problems.

What do you get when you type the following commands:
```
root@edubuntu:/# [COLOR=Red]**ping 64.233.167.99 -c4**[/COLOR]
PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=1 ttl=243 time=33.0 ms
64 bytes from 64.233.167.99: icmp_seq=2 ttl=243 time=33.9 ms
64 bytes from 64.233.167.99: icmp_seq=3 ttl=243 time=35.9 ms
64 bytes from 64.233.167.99: icmp_seq=4 ttl=243 time=33.2 ms

--- 64.233.167.99 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 33.012/34.018/35.905/1.157 ms

root@edubuntu:/# [COLOR=Red]**ping www.google.com -c4**[/COLOR]
PING www.l.google.com (64.233.167.147) 56(84) bytes of data.
64 bytes from py-in-f147.google.com (64.233.167.147): icmp_seq=1 ttl=241 time=33.1 ms
64 bytes from py-in-f147.google.com (64.233.167.147): icmp_seq=2 ttl=241 time=32.5 ms
64 bytes from py-in-f147.google.com (64.233.167.147): icmp_seq=3 ttl=241 time=32.0 ms
64 bytes from py-in-f147.google.com (64.233.167.147): icmp_seq=4 ttl=241 time=32.5 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 32.032/32.548/33.137/0.392 ms

root@edubuntu:/# [COLOR=Red]**ping archive.ubuntu.com -c4**[/COLOR]
PING archive.ubuntu.com (91.189.89.6) 56(84) bytes of data.
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=1 ttl=49 time=120 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=2 ttl=49 time=119 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=3 ttl=49 time=118 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=4 ttl=49 time=118 ms

--- archive.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 118.441/119.270/120.043/0.756 ms
root@edubuntu:/#

```

Post the results here.

Thanks,
Dave

---

### Post by tr3s on 2007-07-07
when im in normal user prompt, i can ping outside the lan, i can connect to the internet. but in chroot i can only ping the local computers and cant ping outside

btw, im using edubuntu as ltsp server and it is just connecting to the internet through a proxy server.

---

### Post by dbott67 on 2007-07-07
> **tr3s said:**
> when im in normal user prompt, i can ping outside the lan, i can connect to the internet. but in chroot i can only ping the local computers and cant ping outside

btw, im using edubuntu as ltsp server and it is just connecting to the internet through a proxy server.

Very strange.  What I'm thinking is this:

The server has a static IP programmed in during installation (by default it's 192.168.0.254), but the clients get a dynamic address from the built-in DHCP server.  If the server has a misconfigured gateway, then it will allow local pings, but will not allow access outside the LAN.

Perhaps your default gateway (aka 'option routers') on the DHCP config file is misconfigured.  Can you post your **/etc/ltsp/dhcpd.conf** file?  Here's mine for comparison:
```
sysadmin@edubuntu:~$ cat /etc/ltsp/dhcpd.conf 
authoritative;

subnet 192.168.[COLOR=Red]1[/COLOR].0 netmask 255.255.255.0 {
  range 192.168.[COLOR=Red]1[/COLOR].201 192.168.[COLOR=Red]1[/COLOR].250;
  option domain-name "example.com";
  option domain-name-servers 192.168.[COLOR=Red]1[/COLOR].1;  [COLOR=Purple]*#<--this is the IP of my D-Link router which has DNS-forwarding built-in*[/COLOR]
  option broadcast-address 192.168.[COLOR=Red]1[/COLOR].255;
  option routers [COLOR=Red]192.168.1.1[/COLOR];   [COLOR=Purple]*#<--this is the IP of my D-Link router.  Compare this line with the output of '[COLOR=Blue]route -n[/COLOR]'*[/COLOR]
  option subnet-mask 255.255.255.0;
  if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
    filename "/ltsp/i386/pxelinux.0";
  }
  else{
    filename "/ltsp/i386/nbi.img";
  }
  option root-path "/opt/ltsp/i386";
}

```The only thing I changed was the 192.168.[COLOR=Red]**0**[/COLOR].xxx to 192.168.[COLOR=Red]**1**[/COLOR].xxx.

Next, from the regular account on the server (not 'chroot'), post the output of the following commands:
```
sysadmin@edubuntu:~$[COLOR=Red] ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:05:5D:07:8D:74
          inet addr:[COLOR=Red]192.168.1.254[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe07:8d74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11784892 (11.2 MiB)  TX bytes:334389 (326.5 KiB)
          Interrupt:9 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5660 (5.5 KiB)  TX bytes:5660 (5.5 KiB)

```
```
sysadmin@edubuntu:~$ [COLOR=Red]route -n[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         [COLOR=Red]192.168.1.1[/COLOR]     0.0.0.0         UG    0      0        0 eth0
```

-Dave

---

### Post by tr3s on 2007-07-09
here's my /etc/ltsp/dhcpd.conf:

```
authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.191 192.168.0.195;
  option domain-name "example.com";
  option domain-name-servers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;
  if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
    filename "/ltsp/i386/pxelinux.0";
  }
  else{
    filename "/ltsp/i386/nbi.img";
  }
  option root-path "/opt/ltsp/i386";
}
```

ifconfig:

```
tr3s@edubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:4A:D1:DC  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe4a:d1dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1782881 (1.7 MiB)  TX bytes:185573 (181.2 KiB)
          Interrupt:19 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12313 (12.0 KiB)  TX bytes:12313 (12.0 KiB)

```

route -n:

```
tr3s@edubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by novabit on 2007-07-12
hi!I'm new in linux and edubuntu but I have everything installed of edubuntu and obtain to make boot in computers of the mark compac. But one will be with computers Pentium 1 already I do not obtain to make boot because it will be? pentium is equipped with VGA S3, 32 Mb of ram and plate of net with PXE

---

### Post by novabit on 2007-07-12
hi!I'm new in linux and edubuntu but I have everything installed of edubuntu and obtain to make boot in computers of the mark compac. But one will be with computers Pentium 1 already I do not obtain to make boot because it will be? pentium is equipped with VGA S3, 32 Mb of ram and ethernet card with PXE

---

### Post by dbott67 on 2007-07-12
@tr3s: Everything looks normal.  The only thing that strikes me is that you mention you connect via proxy server.  Perhaps it has something to do with that.  Sorry that I can't offer any other info.

@novabit: I'm sorry... I don't understand what you're asking.

-Dave

---

