---
title: "How do I map a port?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-04
> Welcome to the µTorrent Port Checker.
A test will be performed on your computer to check if the specified port is opened.

Checking port 17402 on 124.104.4.95...

Error! Port 17402 does not appear to be open.

Please see [www.portforward.com](www.portforward.com) for more information about how to map a port.

Please make absolutely sure that PeerGuardian2 or Protowall is allowing utorrent.com (72.20.34.145) in either of those programs. Those of you using ipfilter.dat should make sure the list does not include the website's IP. After making sure of this, re-run this test by refreshing the page (F5).

I tried portforward.com, but I do not know where to go from there. 

Also, what are PeerGuardian2 and Protowall? Am I supposed to have them?

What happens if I fix all those things? Does the download speed really increase?

---

### Post by RaZer0r on 2007-04-04
yes your download speed will increase because that port is used for passive connections from your torrent program. You probably wont need to open the port on your computer though it's in your router where you need to forward the port to your desktop ip. (or disable the firewall if you installed any)
if you type "ifconfig" in the terminal/konsole you should see some output like this:
```

rein@rein-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:EF:A8:89  
          **inet addr:192.168.0.143**  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1538028 (1.4 MiB)  TX bytes:340053 (332.0 KiB)
          Interrupt:21

```
the bold code is what your desktop's internal ip is (the internal ip is given by the router automaticly i guess)
your router adress will something like it, probably 192.168.0.1 in my case it could be 192.168.1.1 in yours, you'll have to see for yourself.
now if you get the guilde you got with your router, and you open up firefox and enter: [http://192.168.x.1](http://192.168.x.1) you can enter the router settings, and port forwards, from that point, use your manual to check how to forward the port to your desktop computer

---

### Post by amohanty on 2007-04-04
What kind of internet connection do you have?
Are you running behind a router in your home network?

AM

---

### Post by wersdaluv on 2007-04-04
> **amohanty said:**
> What kind of internet connection do you have?
Are you running behind a router in your home network?

AM

I am connected to a wireless lan which is connected to a wired router. The wired router is connected to my dsl.

---

### Post by amohanty on 2007-04-04
Try razor's suggestion and open the port in your router firewall.

AM

---

### Post by anaconda on 2007-04-04
You ubuntu iptables might also be blocking that port.
I had to open my torrent ports from both my alink hardware firewall and from ubuntu iptables.

the easiest way to open a port from ubuntu is to install firestarter and open a port from there.  (it will adjust the iptables.

if your router has a fiewall then you propably need to open that port from it too.

---

