---
title: "IRC server help - hybrid - Maybe port forwarding router"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Henaro on 2007-07-10
Hello~ 

I'm trying to set up a small IRC server for me and my friends.  I have installed ircd-hybrid.  Everything seems to be configured right and I think I forwarded the ports correctly.  I can connect to it locally but when using my IP address Iget a connection refused error in xchat.  

Here's what my forwarded ports are on my linksys router:

App: IRC   

Range: 6000 to 7000 

Protocol: Both UDP and TCP 

IP: 192.168.1._100_

Not sure if I set that up correctly or not.  :(

Thanks for the help!

---

### Post by Malibu Illusion on 2007-07-10
Enter this:

```
sudo ifconfig -a | egrep 192.168.1
```

That will tell you the address of the system you need to forward the ports to.

On a side note, 6000-7000 is quite a broad range to forward.  Typically, you only need to allow a few ports such as 6667 to permit connections to the box, and a few others if you're intending to connect servers to it or allow connections on non-standard ports.

---

### Post by Henaro on 2007-07-10
I have it forwarded to the correct system then.

EDIT:

Although I'm not too sure what Bcast is.  This is what I got:
```

inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

```

---

### Post by greg_g on 2007-07-10
> **Henaro said:**
> 
Although I'm not too sure what Bcast is.  This is what I got:
```

inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

```

BCast is broadcast, the broadcast IP that, well, it doesn't matter what it does for the time being.  Just know that it is a good value.  (I forgot my networking knowledge I learned in my CCNA class in High School).

---

### Post by Henaro on 2007-07-10
Oh I see...

Well I have it forwarded correctly and I'm pretty sure I have it configured correctly.  But I still get the error.  :(

Anyone know of a solution?


Here's from the configuration file:
```

listen {
	/* port: the specific port to listen on.  if no host is specified
	 * before, it will listen on all available IPs.
	 *
	 * ports are seperated via a comma, a range may be specified using ".."
	 */
	
	/* port: listen on all available IPs, ports 6665 to 6669 */
	host = "24.98.20.28";	# change this!
	port = 6665 .. 6669;
};

```

---

### Post by Malibu Illusion on 2007-07-10
192.168.1.100 is the address you need to be entering there, yes.  Traffic should be hitting off your box on those ports.

Try performing a:

```
netstat -l -t | egrep '6667|irc'
```

To ensure it is listening and where.  You may have configured your listen block incorrectly.

---

### Post by Henaro on 2007-07-10
I did that and nothing happened.  :-?

---

### Post by Malibu Illusion on 2007-07-10
Right, try and remove this line entirely from your listen block:

> host = "24.98.20.28";	# change this!

Rehash/restart the server and then try.  This will ensure that it is listening on all of the available interfaces.

---

### Post by Henaro on 2007-07-10
Still the same message:

```
22:26 -!- Irssi: Looking up 24.98.20.28
22:26 -!- Irssi: Connecting to 24.98.20.28 [24.98.20.28] port 6667
22:26 -!- Irssi: Unable to connect server 24.98.20.28 port 6667 [Connection 
          refused]

```

:-(

---

### Post by Malibu Illusion on 2007-07-10
Ironically, I can connect just fine:

> * Looking up 24.98.20.28
* Connecting to 24.98.20.28 (24.98.20.28) port 6667...
* Connected. Now logging in...
* *** Looking up your hostname...
* *** Checking Ident
* *** Found your hostname
* *** No Ident response
* Welcome to the lol Internet Relay Chat Network Malibu
* Your host is henaro_is_cool[0.0.0.0/6667], running version hybrid-7.2.2.dfsg.1-debian-3
* This server was created Dec  6 2006 at 19:21:25
* henaro_is_cool hybrid-7.2.2.dfsg.1-debian-3 DGabcdfgiklnorsuwxyz biklmnopstveIh bkloveIh
* CALLERID CASEMAPPING=rfc1459 DEAF=D KICKLEN=160 MODES=4 NICKLEN=15 PREFIX=(ohv)@%+ STATUSMSG=@%+ TOPICLEN=350 NETWORK=lol MAXLIST=beI:25 MAXTARGETS=4 CHANTYPES=#& :are supported by this server
* CHANLIMIT=#&:15 CHANNELLEN=50 EXCEPTS=e INVEX=I CHANMODES=eIb,k,l,imnpst KNOCK AWAYLEN=160 ELIST=CMNTU SAFELIST :are supported by this server
* There are 0 users and 1 invisible on 1 servers
* I have 1 clients and 0 servers
* Current local users: 1  Max: 1
* Current global users: 1  Max: 1
* Highest connection count: 1 (1 clients) (1 connections received)
* - henaro_is_cool Message of the Day - 
<cut>
* End of /MOTD command.

I don't think I'll display the MOTD message publicly. :P

How exactly are you trying to connect?  Are you permitting *outbound* connections to port 6667 via your router's firewall or iptables (if your policy is restrictive by default)?  Have you connected to any other IRC servers at all on that port and been successful?

---

### Post by Henaro on 2007-07-10
Oh wow.  


Maybe I can't connect locally using my external IP.  I can connect through localhost though.  I'll try to get my friends to connect.

EDIT: Nice it works.  ;D

---

