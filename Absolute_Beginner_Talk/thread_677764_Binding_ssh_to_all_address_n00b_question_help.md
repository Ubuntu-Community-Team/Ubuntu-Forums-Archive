---
title: "Binding ssh to all address? n00b question help"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by skippy_1 on 2008-01-25
I just setup the ssh server and I can connect to it okay if I use my internal LAN address but not the actual internet ip of my machine.
I uncommented the line for "ListenAddress 0.0.0.0" but still nothing! Please help

---

### Post by tribaal on 2008-01-25
You should uncomment listenaddress and then type in the actual address you want to listen on, not 0.0.0.0.

I.e:
ListenAddress 192.168.0.5

Hope this helps :)

- Trib'

---

### Post by skippy_1 on 2008-01-25
Ok, I've gone to whatismyip.com, taken the ipaddress from there and put that in my listen thing. Still unable to connect, it just does nothing, no password prompt or anything

---

### Post by hyper_ch on 2008-01-25
what is your network setup like?

---

### Post by ByteJuggler on 2008-01-25
> **skippy_1 said:**
> Ok, I've gone to whatismyip.com, taken the ipaddress from there and put that in my listen thing. Still unable to connect, it just does nothing, no password prompt or anything

That will only work if that IP is actually your PC's IP.  If it is e.g. your router's IP then it won't work without additional setup.   Open a terminal window and enter 

```
ifconfig
```

Check the "eth0" entries, look for your IPv4 address.  If it matches the one from whatismyip.com, then we have to figure out why you can't connect (possibly firewall?)  If it does not match (it'll typically then be something starting with 192.168.x.x or 10.0.x.x), then you probably have a "NAT" router, and your PC's address is not the same as the one on whatismyip.com.

---

### Post by skippy_1 on 2008-01-25
This is my home box, I've got broadband and no hardware firewall of my own.
To use the broadband I'm pretty sure I connect to my ISP's router and get my internet address assigned from there.
I considered that possibility that my ports are being blocked by the ISP but on this very port I've gotten ktorrent's webadmin to work (when port forwarding was checked). I also have no problem with my apache webserver and the like so the ports cannot be blocked.

When off the internet, I'm on a local LAN of sorts. This address also I can ssh to besides localhost.

---

### Post by ByteJuggler on 2008-01-25
> **skippy_1 said:**
> This is my home box, I've got broadband and no hardware firewall of my own.
To use the broadband I'm pretty sure I connect to my ISP's router and get my internet address assigned from there.
I considered that possibility that my ports are being blocked by the ISP but on this very port I've gotten ktorrent's webadmin to work (when port forwarding was checked). I also have no problem with my apache webserver and the like so the ports cannot be blocked.

When off the internet, I'm on a local LAN of sorts. This address also I can ssh to besides localhost.

The fact you mention "port forwarding" means you're running a NAT router.  Have you port forwarded SSH's port (port 22)?

---

### Post by skippy_1 on 2008-01-25
I was under the impression that the #ListenAddress thing did that already. If not then how do I setup port forwarding?

---

### Post by SomethingCronic on 2008-01-25
It sounds like you have either a modem attached to a router, or an all in once modem/router. If this is the case run :

```
ifconfig
```

in an Ubuntu terminal. along eth0/eth1 you should see an IP address such as 172.18.x.x or 192.168.x.x

If this is the case you almost definatly have a router with it's own private address range.

Typically, you will then need to configure the router to forward ports to the specific PC. You router is 'usually' the first IP of that range - so if you're PC is 192.168.2.2 then the router is likely to be 192.168.2.1

Type [http://192.168.2.1](http://192.168.2.1) into your web browser and you should hopefully be prompted for a username/password. If you don't know this then I would suggest you look up the router make/model on the net and see if the default username password work. 

If you can get this far, then get back to us and I'm sure between us all we can figure out how to setup the forwarding on your router.

Regards,
Mike

---

### Post by ByteJuggler on 2008-01-25
> **skippy_1 said:**
> I was under the impression that the #ListenAddress thing did that already. If not then how do I setup port forwarding?

Port forwarding is done on your router.  If your PC is on a private LAN that is NAT'ed to the public internet, then you need to similarly port forward port 22 on your router (from its public IP address) to your PC's local LAN private address. 

For your webserver to work you must've already done this for it (port 80).  What/What did you do to make that work?

Normally you can set up port forwarding by using your router's web interface.

---

### Post by The Cog on 2008-01-25
A listenng address of 0.0.0.0 means listen on all local addresses. This is the address you need in the SSHD configuration file. The command 
**netstat -lnt**
will tell you what's listening. You should see an entry like one of these two lines (either is OK):
> tcp6       0      0 :::22                   :::*                    LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN

Check that your address on your machine is the same as the one that whatismyip.com says. Use the command 
**ifconfig**
and look at the inetAddr line. If it doesnt't match your address that whatismyip.com says, then you have a router or something between you and the internet and you will have to configure that to pass TCP port 22 on to your local address.

---

### Post by skippy_1 on 2008-01-25
Sorry for responding so late, got cut off.

Neither netstat -lnt nor ifconfig show the actual IP of my computer on the internet, just the LAN.
And the router that's in the way belongs to my ISP so I can't make changes to it.
However when I just click on enable port forwarding, I can access my ktorrents web interface from the internet at the actual IP. Even when using that same port for ssh, I can't get through :(

---

### Post by ByteJuggler on 2008-01-25
> **skippy_1 said:**
> Sorry for responding so late, got cut off.

Neither netstat -lnt nor ifconfig show the actual IP of my computer on the internet, just the LAN.
And the router that's in the way belongs to my ISP so I can't make changes to it.
However **when I just click on enable port forwarding, **I can access my ktorrents web interface from the internet at the actual IP. Even when using that same port for ssh, I can't get through :(

What do you mean "I just click on enable port forwarding"?  Click where?  

Normally with most broadband services, whether or not they supply the router, you can access the router's configuration pages, to control things like port forwarding and so on.  

What ISP are you with exactly and what router do you use exactly?

---

