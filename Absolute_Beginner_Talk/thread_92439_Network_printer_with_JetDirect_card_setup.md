---
title: "Network printer with JetDirect card setup"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by walkabout on 2005-11-19
I installed Ubuntu 5.10 and everything works well, except for my printer. I have:
-Wireless Netgear router WGT624 connected to Internet (I can access Internet with my wireless card).
-printer HP4000 with JetDirect J3110A card is connected to the router
-printer's IP:192.168.0.100, SM: 255.255.255.0, Gateway:192.168.0.1
-My Router has LAN IP 192.168.0.1 and has DHCP server enabled with range 192.168.0.2-192.168.0.254. As I can see, it only has SPI (Stateful Inpection) Firewall (protects your LAN against Denial of Service attacks). In attached devices it only shows one with 192.168.0.2 - presumably my Ubuntu box.

I have tried all kinds of tricks to setup this printer that I can find on this forum with no success. Then I discovered I can't ping printer's IP, so this is very strange since Windows would print on the same setup with no problem. I removed windows and now cannot check if pinging IP was working on it. Can anyone give me suggestions on how to resolve this problem?

---

### Post by suRoot on 2005-11-19
The firewall is not an issue here as both your PC & printer are on the same LAN segment.

I assume that since you're posting the network connection works on your Ubuntu box.  I assume you can ping 192.168.0.1?  If neither of those are the case then you most likely have a problem with your PC & not the printer.

I've never seen a jetdirect card reject ICMP (ping), but just for the sake of being thorough, what happens when you 

```
telnet <ip of printer> 9100
```

from a console?

Can you verify the cables are properly attached to the printer & that you have a link light on the jet direct card (should be a green light near the ethernet port).  You may also want to print out the configuration menu (just cycle through the printer menus until you find this option) to make sure the IP is actually what you think it is.

As for setting up the printer, it's pretty straightforward:

Menu -> system -> administration -> printing -> new printer

Printer Type:  Network Printer (HP JetDirect)
Host:  IP of printer
Port:  9100

Click Next

Manufacturer:  HP
Model:  Your model
Driver:  hplj

Click Apply

That's it.

---

### Post by walkabout on 2005-11-19
Hi,

I get:
alex@walkabout:~$ telnet 192.168.0.100 9100
Trying 192.168.0.100...
telnet: Unable to connect to remote host: No route to host

Also, my JetDirect card dosn't have any lights, I can see green light on the port of the router where it is connected.

My printer IP is confirmed. but I can't ping it. I can ping 192.168.0.1 and connect to internet right now.

I instal the printer as per your instraction yet, test page just sit there with no error at all

---

### Post by suRoot on 2005-11-19
Just a few more things for you to try:

- If you have another PC, laptop, whatever, see if you can ping the printer from that machine.

- If you can telnet to your roter, do so - log in and try to ping the printer from the router.  Some routers have a utility which will ping a host from their web interface so you may see if this is the case with your model.

- Try plugging the printer in to another port on the router.

- Double check the config on your printer.  Make sure the subnet mask matches that of your ubuntu box (you can see this on the ubuntu box by running ifconfig eth0 from a console.  It will be listed as "mask")

- Try re-seating the jet direct card.  I'm assuming it's internal since you say it has no lights.  You should see one screw at the top and one at the bottom of the card.  Use a screwdriver to remove them & pull the card out of the printer.  Re-insert it, tighten the screws & power on the printer.

- Try a new cat5 cable from the printer to the router.

---

### Post by walkabout on 2005-11-19
well, here is the fun part - I can see this printer and print from old Mac laptop using its ethernet port (system 9). So, there is no problem with router unless maybe JetDirect card is too old (printer is about 5 years old) so Ubuntu maybe dosn't support it..

The problem then with my Ubuntu.

How about this - when I run nmap print_server_ip
I get this
Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-19 15:58 PST
Failed to resolve given hostname/IP: print_server_ip.  Note that you can't use '/mask' AND '[1-4,7,100-]' style IP ranges
WARNING: No targets were specified, so 0 hosts scanned.
Nmap run completed -- 0 IP addresses (0 hosts up) scanned in 0.225 seconds

is this normal? (I don't know if print_server_ip is applyed to JetDirect..)

Should I reinstal system?

---

### Post by suRoot on 2005-11-19
No need to reinstall...

nmap -sS 192.168.0.100 would be the command I used.  It looks like you ran nmap against "print_server_ip" which apparently doesn't resolve to an IP address.

Please verify that you tried the other things I suggested.  Also, open a console & paste the output from

```
ifconfig eth0
```

as well as 

```
route
```

(not that it should even matter on a LAN)

---

### Post by walkabout on 2005-11-19
Yes, I have tried it. Here are all the runs:

nmap -sS 192.168.0.100
You requested a scan type which requires r00t privileges, and you do not have th em.

sudo nmap -sS 192.168.0.100

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-19 16:16 PST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap run completed -- 1 IP address (0 hosts up) scanned in 2.106 seconds

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 ath0
default         192.168.0.1     0.0.0.0         UG    0      0        0 ath0

ifconfig eth0
eth0: error fetching interface information: Device not found

ifconfig
ath0      Link encap:Ethernet  HWaddr 00:09:5B:95:0D:49
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe95:d49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3045 errors:3322 dropped:0 overruns:0 frame:3322
          TX packets:3882 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:2191522 (2.0 MiB)  TX bytes:536935 (524.3 KiB)
          Interrupt:11 Memory:d0b00000-d0b10000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5718863 (5.4 MiB)  TX bytes:5718863 (5.4 MiB)

---

### Post by walkabout on 2005-11-21
any ideas anybody? I guess my box is missing some network settings, but how do I fix/set it?

Please help

---

### Post by janrinok on 2005-11-22
I think that you have a configuration problem.  Your ethernet card is usually eth0, eth1 etc but if config cannot find it.  However, you appear to have a card that you have named 'ath0' - have you typed this name in yourself because it looks like a typo.  Try renaming your card 'eth0' and restart the network.


Your data

........
192.168.0.0 * 255.255.255.0 U 0 0 0 ath0
default 192.168.0.1 0.0.0.0 UG 0 0 0 ath0

ifconfig eth0
eth0: error fetching interface information: Device not found

ifconfig
ath0 Link encap:Ethernet HWaddr 00:09:5B:95:0D:49
.......

---

### Post by janrinok on 2005-11-22
Sorry, just to avoid the confusion, I should have typed 'ifconfig cannot find it'!

---

### Post by ed_d on 2005-11-22
Can you acces your routers menu via a browser? YOu can verify that the printer is actually being see. Also, do you have the printers jet-direct card with a static IP?

---

### Post by walkabout on 2005-11-25
I now know that it is a problem with my JetDirect card, it is simply does not work with IP address. I bought this printer 5 years ago and I am sure newer JetDirect cards work better.

I installed Win2000 and was able to print using IPX protocol, but not TCP/IP
I can't ping printers IP from windows, also I am able to print on it (using JetAdmin on IPX, interestingly JetAdmin wouldn't see printer if IPX protocol is not installed).

To make myself filling better, I installed Ubuntu at my work and was able to print to network printer using its IP address right away:cool:

Thak you all for your help

---

