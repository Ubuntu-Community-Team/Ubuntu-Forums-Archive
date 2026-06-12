---
title: "Vnc, is this safe?"
date: 2013-04-29
forum: Any Other OS
---

### Post by CaptainMark on 2013-04-29
I been looking into VNC today, I've never had to use it before so I know nothing about it but my mum asked me to install Linux Mint on her laptop so I'm sure I'll be needing it. 

What I need is to someone who knows the field to just give me the green or red light if my method is safe to use, I know VNC over the internet can be a bit of a touchy subject with regards to security.

I'm fairly comfortable with ssh, so I already have a secure connection established with ssh (no password, rsa keys etc.) lets assume here that the ssh connection is safe and sound so we don't get off topic. Anyway here's a quick run-down of what I think is okay.

Server:
I've opened up Vino (the standard vnc server in Mint, I think ubuntu too) and chosen to share my desktop with others and allow control of it, I've selected the option so the server has to authorise each connection to allow any vnc session (no password, I'll probably only ask her to turn this on as and when we need it).

Client: (eeepc is my test host)
I've installed Remmina to use as a client. My first step here is to forward a ssh port ```
ssh -L 2808:localhost:5900 eeepc
```then I've opened remmina and used localhost as a server with port 2808 (randomly chosen)

The connection request then pops up on the server and after mum clicking connect then I've started my own remote IT help desk, great.

So the big question, is this safe, green light or red light? At least in the terms of general home use (excluding the risk of high-profile attacker targeting my dear old mum)

Many Thanks 
Regards
Mark

---

### Post by steeldriver on 2013-04-29
It's not necessarily unsafe (since presumably your mum's router will NOT be port forwarding anything to her port 5900) however if you are going to insist on ssh tunneling you may as well tell the VNC server only to accept connections from localhost so that 5900 is actually closed - just creating the tunnel doesn't do that, afaik

For the default vino-server that option seems to have been omitted from the GUI so you need to dig into dconf to get to it - either by installing the graphical dconf editor or via the command line as

```
dconf write /desktop/gnome/remote-access/network-interface "'lo'"
```

This would give a layer of protection even if someone got inside her LAN (in addition to any firewall that you are running on the machine).

[DISCLAIMER: I am *not* an expert - this is just a result of my own experiments]

---

### Post by Perfect Storm on 2013-04-29
Moved to Other OS/Distro Support.

---

### Post by CaptainMark on 2013-04-29
So does Vino open port 5900 dy default, messing around with an online port checker would suggest it does, even without the upnp option ticked in vino preferences

---

### Post by CharlesA on 2013-04-29
+1 to setting VNC to listen to localhost. It is a very good idea to tunnel it over SSH, which is what you are attempting to do. :)

> **CaptainMark said:**
> So does Vino open port 5900 dy default, messing around with an online port checker would suggest it does, even without the upnp option ticked in vino preferences

Check:
```
sudo netstat -nlp
```

---

### Post by markbl on 2013-04-29
> **CaptainMark said:**
> So does Vino open port 5900 dy default, messing around with an online port checker would suggest it does, even without the upnp option ticked in vino preferences
OP, your first post here is quite detailed but omits something very important. We assume your mothers laptop is behind her home router. So have you set only 1 port forward on that to forward ssh to her laptop? If that is the only port forward you have set in the router (forget about ssh port forwarding at the moment), and you have turned off upnp in Vino, then it is irrelevant whether Vino opens port 5900 etc on her laptop. Of course when you ssh from an external site then that address "eeepc" in your example will be the external IP address of your mum's router. This is often a dynamic address for home connections so most of us use a free service like dyndns.org, noip.com, etc.

Personally, I set a port forward in my router from external port 443 to my server port 22. I recommend this because it allows you to ssh out on port 443 when you are in a corporate/work environment where the corporate firewall often blocks port 22 outbound. Port 443 is harder to block (used for ssh here instead of the usual https), I've never seen one that does.

---

### Post by CaptainMark on 2013-04-30
@CharlesA Okay I piped that through grep for 5900 and it does ask for port 5900 to be open even without the upnp option enabled

@markbl Yes I should have mentioned, I haven't done anything yet to my mum's router, but when it comes to it, I'll only be forwarding the one port and it will be a totally random non-standard port to stop those pescky basic attack bots flooding the pc with half arsed attempts.

Okay I'm pretty comfortable that this will be safe enough for general home purposes, all I need to get done is stop Vino from opening port 5900, I'd prefer to have absolutely no unnecessary ports open. I assume that was what Steeldriver mentioned but I'm off to work right now so I'll look into that tonight.

Many thanks so far

---

### Post by CharlesA on 2013-04-30
There should be an option for it to only allow local connections, which should limit it to localhost.

This might help:
[http://ubuntuforums.org/showthread.php?t=1995563](http://ubuntuforums.org/showthread.php?t=1995563)

---

### Post by CaptainMark on 2013-04-30
Okay thanks for your help, I've followed that thread on my Ubuntu test rig and the netstat command still reports that vino is listening on port 5900 but an online port checker is reporting that 5900 is closed, so I guess this is maybe what I want??? I'm a touch confused, is it correct that netstat still reports vino listening on 5900 but only allowing connections from localhost?

EDIT:
I just done a quick google how to ping a specific port and got the tip to use nmap so this might help clarify, this is vino running```
mark@desktop ~/ $ nmap -p 5900 127.0.0.1

Starting Nmap 6.00 ( http://nmap.org ) at 2013-04-30 18:59 BST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000023s latency).
PORT     STATE SERVICE
5900/tcp open  vnc


Nmap done: 1 IP address (1 host up) scanned in 0.03 seconds



```This would indicate that the port is open?? Im not sure, I'm not a expert on networking, I will try pinging from another pc

2ND EDIT: nmap from another pc shows the port as closed so I guess I'm safe here. I'll close this one unless anyone sees any glaring security issues which I dont know about

Many Thanks

Cap'n

---

### Post by mips on 2013-04-30
Anything connected to the internet is the devils spawn! Be gone satan!

---

### Post by steeldriver on 2013-04-30
Mark I think the distinction is that you are explicitly specifying the loopback interface IP (127.0.0.1) - if you specify the machine's LAN IP (i.e. its *external *interface) then you should see 'Closed' if vino-server is configured to listen only on localhost, e.g.

```
$ sudo ufw disable
[sudo] password for steeldriver:
Firewall stopped and disabled on system startup
$
$ sudo nmap -p 5900 **127.0.0.1**

Starting Nmap 5.21 ( http://nmap.org ) at 2013-04-30 19:36 EDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000079s latency).
PORT     STATE SERVICE
**5900/tcp open  vnc**

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
$
$ sudo nmap -p 5900 **192.168.1.12**

Starting Nmap 5.21 ( http://nmap.org ) at 2013-04-30 19:37 EDT
Nmap scan report for 192.168.1.12
Host is up (0.00015s latency).
PORT     STATE  SERVICE
**5900/tcp closed vnc**

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
$

```

Now if I revert vino-server to the default config we see the port becomes open on the external iface as well:

```

$ **dconf reset /desktop/gnome/remote-access/network-interface**
$
$ sudo nmap -p 5900 **192.168.1.12**

Starting Nmap 5.21 ( http://nmap.org ) at 2013-04-30 19:40 EDT
Nmap scan report for 192.168.1.12
Host is up (0.00014s latency).
PORT     STATE SERVICE
**5900/tcp open  vnc**

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds

```

Once I tell the server only to listen on localhost the port appears closed on the external iface again:

```

$ dconf write /desktop/gnome/remote-access/network-interface "'lo'"
$
$ sudo nmap -p 5900 **192.168.1.12**

Starting Nmap 5.21 ( http://nmap.org ) at 2013-04-30 19:46 EDT
Nmap scan report for 192.168.1.12
Host is up (0.00013s latency).
PORT     STATE  SERVICE
[B]5900/tcp closed vnc
[/B]
Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds

```

Hope this helps

---

### Post by CaptainMark on 2013-05-01
Yes it does help, I didn't know there would be a difference, I've always just thought localhost and 127.0.0.1 was shorthand for 'this computer' but what your saying makes perfect sense, I'm sure this will come in handy for many things in the future as well.

Thanks for the help everyone

Regards
Mark

---

