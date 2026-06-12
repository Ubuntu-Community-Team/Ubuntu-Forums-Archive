---
title: "A seemingly unique problem"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Cilionelle on 2007-03-11
I've installed Ubuntu 6.10, have managed to get the World Wide Web displayable via Firefox, but am having problems getting the software updates to work.  Can someone help me please?

---

### Post by scxtt on 2007-03-11
what're you trying to do? (what commands / programs are you using?)
make sure you can do "sudo apt-get update" to sync w/ the software repositories ...

---

### Post by Cilionelle on 2007-03-11
That's what I've been trying to do, mostly through Synaptic and Ubuntu's own updater.  I just tried the "sudo apt-get update" (which is essentially the same as those others, just at a prompt, right?) and got the same message:

> Could not connect to 192.168.1.1:8080 (192.168.1.1). - connect (111 Connection refused)

That IP address is the router I'm using.

---

### Post by scxtt on 2007-03-11
what is the output of **ifconfig**?

---

### Post by Cilionelle on 2007-03-11
eth0      Link encap:Ethernet  HWaddr 00:0D:56:38:01:46  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe38:146/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:267753 (261.4 KiB)  TX bytes:35997 (35.1 KiB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by Cilionelle on 2007-03-11
I'll take it that this means that no-one has any idea what is going on... sigh!

---

### Post by scxtt on 2007-03-11
any ideas why it's trying to connect to port 8080?  that's generally the "remote management" port - for changing router configs from outside your network ...

---

### Post by Cilionelle on 2007-03-11
I have no idea.  I have only just installed (as in plugged in the cables and checked it works in Windows) the router, but I have not much of an idea why it would be doing that.  Any simple (ha!) solutions?  I'd really like to get this sorted ASAP.  (PS: Thanks for your help, scxtt.)

---

### Post by 3rdalbum on 2007-03-11
Is port 8080 open to outbound traffic on your router's firewall?

---

### Post by scxtt on 2007-03-11
2 ideas:

1. what is in the file **/etc/resolv.conf**?
2. can you disable "remote management", port 8080 after connecting to your router?

---

### Post by Cilionelle on 2007-03-11
The only thing in /etc/resolv.conf is: "nameserver 10.1.1.1"

As to disabling the 8080 remote management, no idea how to do that!  How do I do it?

---

### Post by scxtt on 2007-03-11
to disable port 8080 (if you don't intentionally use it, you don't need it):

open a browser and enter **[http://192.168.1.1](http://192.168.1.1)** (you'll have to know the admin password of your router, if you've NEVER changed it or logged in, it's probably "admin" or "administrator") ... then look through the web interface for mention of 8080 and disable it ...

also, while you're in there - look for the IP addresses for your ISP's DNS ... should be kinda obvious when you find them ... you'll need them to put in "resolv.conf" (as a temp solution, try putting **nameserver 192.168.1.1** in /etc/resolv.conf) ...

then do: sudo /etc/init.d/networking restart

---

### Post by msak007 on 2007-03-11
If your IP is in the 192.168.x.x range, then your router's IP is most likely 192.168.1.1 and that's the address that should be in the resolv.conf file. Not sure what 10.1.1.1 is and where it came from. Can you post the contents of the file **/etc/apt/apt.conf**?

---

### Post by Cilionelle on 2007-03-11
/etc/apt/apt.conf is an empty file.
looking at my router settings, 10.1.1.1 is listed as the default gateway IP address, the domain name server 1 and the DHCP server.  The intranet's Private IP address is the 192.168.1.1 and the Public IP address is 10.1.1.2

Does that answer your q's?

---

### Post by scxtt on 2007-03-11
the whole setup seems strange to me, as if it's mixing 2 reserved sets of IPs together ... not being able to see it, i'm not sure i'd want to suggest changes ...

---

### Post by Cilionelle on 2007-03-11
The "changing the /etc/resolv.conf" suggestion didn't work out.  I still get the same error, not able to connect.  Since 10.1.1.2 is the public IP address for the internet, would changing it to that help?  And are there any other places it needs to be changed for it to work?

---

### Post by scxtt on 2007-03-11
well, the way mine is set up it's all based off 192.168.1.1

my box's IP is 192.168.1.100 which is based of the 192.168.1.1 IP of my router which connects to my cable modem (which uses my "external IP", what i type from the outside to connect to my PC from any computer that's not in my network) ...

now i could change my router's IP to 10.1.1.1 and use 10.1.1.100 for my PC - but i don't understand why you've got a mixture of 192.168.1.1 and 10.1.1.1 ...

are you able to connect to 192.168.100.1 or 10.1.100.1?  if i do that i can connect to the router itself (no p/w required) where i can see a few bits of info (like my external IP) ...

---

### Post by Cilionelle on 2007-03-11
Neither of the IPs you listed are working for me on this router.  I'll try some different combinations, though, unless you've got some more ideas (anything is better than "Um, how do I reinstall Windows?")

---

### Post by scxtt on 2007-03-11
i don't have any more ideas that don't involve me actually seeing your router's config ... :(

---

### Post by msak007 on 2007-03-11
> **Cilionelle said:**
> /etc/apt/apt.conf is an empty file.
looking at my router settings, 10.1.1.1 is listed as the default gateway IP address, the domain name server 1 and the DHCP server.  The intranet's Private IP address is the 192.168.1.1 and the Public IP address is 10.1.1.2

Does that answer your q's?
Well if 10.1.1.1 is your router's default gateway, your machine will pick that up when it connects to your router. There's no need to hardcode that into your config file, and you should change it to match your router's IP. Now I'm not entirely sure that's the problem as apt is the only app having the problem (that you know of) and Firefox connects just fine. Not sure if the file is read automatically or if you have to restart your network, so once you've done that you can try to reload your network just to make sure:
```
sudo /etc/init.d/networking restart
```If you use Network Manager to connect, just ignore all the DHCP errors in the output and then reconnect once your device is back up.

This all seems very odd, I've installed variants of Ubuntu on many machines and have never had this issue.

EDIT: I searched a little, and it seems you may have some sort of proxy set up preventing apt from connecting. I just found [this]("http://www.ubuntuforums.org/showthread.php?t=352877&highlight=apt+8080") thread - pay attention to step # 9 specifically and check to see if you have a proxy set up.

---

### Post by HereInOz on 2007-03-11
You say that you have the Internet working, but from your configuration details, and what you have said, I am beginning to doubt it.

Can you try two things:

Open a terminal and type in:    ping 66.102.7.147

If your internet connection exists, then you should get a response.

Then, close that terminal, and re-open one, and type it:   ping [www.google.com](www.google.com)

If you get a response to that, then your internet is indeed working correctly, but if not, then you have a problem with it.

If the first ping responds, but the second does not, then it is a DNS issue, but if neither respond, you are not connected at all.

See what happens and let us know.

---

