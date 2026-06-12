---
title: "Connecting to Windows from Linux"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by pjbishop on 2005-12-31
Hi there,

I'm trying to connect to my windows box from Ubuntu and cannot seem to ping the windows box.

Originally ping gave me an error "Network is unreachable" - after some head scratching and googling I fixed this by making my card the default connnection (via "route add default eth0")

Now ping seems to work as the light by the network cable flashes on the windows box but no response is recieved on the linux box

any suggestions for my next steps?

TIA

Paul

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=pjbishop]Hi there,

I'm trying to connect to my windows box from Ubuntu and cannot seem to ping the windows box.

Originally ping gave me an error "Network is unreachable" - after some head scratching and googling I fixed this by making my card the default connnection (via "route add default eth0")

Now ping seems to work as the light by the network cable flashes on the windows box but no response is recieved on the linux box

any suggestions for my next steps?

TIA

Paul[/QUOTE]

Does your Windows box have a Firewall?  What about your Ubuntu box?
What do the routing tables on your Windows PC and Ubuntu PC look like?
```

c:\> route print

$ route

```

---

### Post by purpleturtle on 2005-12-31
I had this problem.. You could try temporarily turning off the firewall on the windows machine to confirm the firewall is the problem.

As it happens, I found that turning off "simple file sharing" on the windows machine enabled me to ping it.. Doing this must tweak the firewall settings to allow pings through.  (I did this through Explorer / Tools / Folder Options / View ...)

---

### Post by pjbishop on 2006-01-01
this is the o/p from 'route print'

don't know how to interpert it - can anyone help

- actually I haven't explicity set the ip on the linux box (I thought DHCP would assign this - is this correct)

===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 50 56 c0 00 01 ...... VMware Virtual Ethernet Adapter for VMnet1
0x3 ...00 04 23 97 20 89 ...... Intel(R) PRO/Wireless LAN 2100 3B Mini PCI Adapter - Net Firewall Miniport Interface
0x4 ...00 0d 60 2f 98 6c ...... Intel(R) PRO/1000 MT Mobile Connection - Net Firewall Miniport Interface
0x5 ...00 20 e0 4b 7a 16 ...... Bluetooth LAN Access Server Driver - Net Firewall Miniport Interface
0x40006 ...00 00 00 00 00 01 ...... AGN Virtual Network Adapter - Net Firewall Miniport Interface
0xc0008 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    81.146.43.190   81.146.43.190       1
    81.146.43.190  255.255.255.255        127.0.0.1       127.0.0.1       50
   81.255.255.255  255.255.255.255    81.146.43.190   81.146.43.190       50
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      169.254.0.0      255.255.0.0  169.254.110.122  169.254.110.122      10
  169.254.110.122  255.255.255.255        127.0.0.1       127.0.0.1       10
  169.254.255.255  255.255.255.255  169.254.110.122  169.254.110.122      10
    192.168.233.0    255.255.255.0    192.168.233.1   192.168.233.1       20
    192.168.233.1  255.255.255.255        127.0.0.1       127.0.0.1       20
  192.168.233.255  255.255.255.255    192.168.233.1   192.168.233.1       20
     217.32.59.74  255.255.255.255    81.146.43.190   81.146.43.190       1
        224.0.0.0        240.0.0.0  169.254.110.122  169.254.110.122      10
        224.0.0.0        240.0.0.0    192.168.233.1   192.168.233.1       20
        224.0.0.0        240.0.0.0    81.146.43.190   81.146.43.190       1
  255.255.255.255  255.255.255.255  169.254.110.122  169.254.110.122      1
  255.255.255.255  255.255.255.255    192.168.233.1           40006       1
  255.255.255.255  255.255.255.255    192.168.233.1               3       1
  255.255.255.255  255.255.255.255    192.168.233.1               5       1
  255.255.255.255  255.255.255.255    192.168.233.1   192.168.233.1       1
Default Gateway:     81.146.43.190
===========================================================================
Persistent Routes:
  None

---

### Post by Nightwind on 2006-01-01
[QUOTE=pjbishop]Hi there,

I'm trying to connect to my windows box from Ubuntu and cannot seem to ping the windows box.

Originally ping gave me an error "Network is unreachable" - after some head scratching and googling I fixed this by making my card the default connnection (via "route add default eth0")

Now ping seems to work as the light by the network cable flashes on the windows box but no response is recieved on the linux box

any suggestions for my next steps?

TIA

Paul[/QUOTE]
What version of Windows?
I am not good at explaning this but I will try my best and hope it helps.
On my XP Pro SP-2 box I have to put the IP address of the Ububtu box in the exceptions dialog box on the windows machine firewall control box. Go to start, settings, control panel, firewall,exceptions, to do this.
This tells windows that it's ok to talk to this IP adress. It makes it easier if all of the machines have to have the same subnet (example 255.255.255.0)
I have also added a share(a user account for lack of a better term)on the XP box. Keep in mind that only 10 users can log into a XP box at any given time. This user name is the same as the log in on the Unbuntu box same password.
I would also set all the I.P addresses,subnet, use the DNS that your ISP provides or is showing in the properties box. I do this myself simply because they change when the machine is turned off and back on is some cases. Make sure that they are all members of the same group:example JoeDoe.

---

### Post by pjbishop on 2006-01-01
I'm using XP 

Trouble is I'm not sure if i've set the ip address on the linux box correctly

If I go to the network setting app and view properties  the config is setup as DHCP

I've tried that and set a static ip address and allowed that though the firewall - no joy - the light by the xover cable blinks but no response is received on the linux box (I don't have a firewall on that as it not connected to the internet)

---

### Post by Nightwind on 2006-01-01
I'm going to fire up my network here and check something and will try to help. Be patient as I am new to Linux but not Windows.

---

### Post by deNoobius on 2006-01-01
One small suggestion--there's a small program called nmap (it's in the repositories) that runs in the command line that you can use to ping and return information on your entire network, including the IP and name of each machine.  It's very handy for just what you're trying to do.

You would install it and type at the command prompt: sudo nmap -sP [the first three elements of your network IP].*

For instance, for me its:  sudo nmap -sP 192.168.1.*

That command returns the address of my router and the address and name of each machine on my network, including the home machine.



Another thing is (you may already have this covered) but you can try marking specific folders for sharing on the XP box.  That's how I do it, rather than trying to lower the firewall.  Doing so will create the necessary exception in the firewall.  If you are also using a third-party firewall like zonealarm you might want to turn it off.

---

