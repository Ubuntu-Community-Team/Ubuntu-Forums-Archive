---
title: "Possible Firewall problem"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by MyBigToe on 2006-08-12
Im trying to forward ports for Azureus, but they always come up as NAT Error.
Ports which have always worked with utorrent in windows dont work either, my IP is the same (192.168.1.2) and I use a hardware firewall, so i dont need a software one, 
Is there one included with ubuntu 6.06 that i might inadvertantly be using?
If so, how can i check? and more importantly, stop it from running at start or if needed, open the port i use?

---

### Post by kebes on 2006-08-12
As far as I know, a standard Ubuntu install does not have any firewall running.

You can use a commandline program called "nmap" to probe a given IP-address. It will tell you what ports are open/responding. Use it on yourself and you'll get an idea of what's going on.

You can also use "ping" to check these things. Try "ping localhost" and then "ping 192.168.1.2" ... do they give the same result?

I know you said that your IP-address didn't change... but double-check this! run "ifconfig" and see what devices are enabled, and their IP-addresses. Is it possible that you have multiple network interfaces defined? (typically you should have "eth0" which is your ethernet card and "lo" which is a loopback interface... if you have entries for hardware devices that don't exist this is a problem!)

I know those suggestions are not very specific. Maybe they'll uncover something, though.

---

### Post by MyBigToe on 2006-08-12
using ifconfig, yep, my IP address is 192.168.1.2
nmap, using the line 
nmap 192.168.1.2 -p48000
gave me the reply
48000/tcp closed unknown

I have opened it to both TCP and UDP 
as shown in the image

---

### Post by kebes on 2006-08-12
It shounds like you're doing everything right.

Other things to try:
1. Is the result of nmap the same whether you have Azureus running or not?

2. Do you have any other bt-client installed? If so, do they all get the same errors on those ports? That is, are you sure it is an OS-level port problem, and not an application issue?

---

### Post by MyBigToe on 2006-08-12
ive used Bittornado and Bittorrent with the same problem (and utorrent through wine)

and yes, same result with or without any BT client running

---

### Post by kebes on 2006-08-12
If you never explicitly set-up a firewall rule against traffic on those ports, I don't see why there would be a problem. However you could certainly check on the status of your iptables settings, and see if for some reason those ports are blocked. Try:
$ sudo iptables -L

And see what it says. "Firestarter" is a nice interface to configuring iptables rules. You could install that if you like.

If iptables indicates some sort of port blocking policy, you can of course modify it. But like I said by default it should look empty.


If iptables is empty (which it probably is), then the only reason I can see for nmap returning "closed unknown" is that the application is not really listening on that port. Go into the settings for Azureus and double-check that it is really using the port range you think it is. (I know this is obvious and you've probably already done it a hundred times...)

---

### Post by MyBigToe on 2006-08-12
i have no idea why, but its actually working now.
The only thing ive done since (that might have made a difference) is restart, but ive done that many a time since.
Hmm.. i cant think of a reason for that.

Thankyou for your help and thanks for helping us newbies.

---

