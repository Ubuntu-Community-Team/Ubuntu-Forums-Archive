---
title: "Why can't i telnet out of port 6000?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by natan- on 2006-08-09
I am trying to connect to a server using ubuntu. So I type this into the console:

telnet 216.98.58.100 6000

And I can't get through and I dont have any firewalls active that I know of just a router. You are welcome to try it out for yourself, you should get some jibberish text on connect.  How would I troubleshoot what is keeping me from connecting?

---

### Post by MaximB on 2006-08-09
I think that is b/z the telnet service is closed by default
you have to client but you need to enable the service.

---

### Post by natan- on 2006-08-09
I can telnet to other servers, just not ones on port 6000. For example I can telnet into my router on port 23 just fine. But when i try to get this one on port 6000 it says:

telnet 216.98.58.100 6000
Trying 216.98.58.100...
telnet: Unable to connect to remote host: Connection timed out

---

### Post by MaximB on 2006-08-09
mmm... don't know about this
but say : did you "started" or "enabled" the telnet service ?
cuz if it was enabled - well...I've already posted a thread about this telnet subject...

---

### Post by natan- on 2006-08-09
Telnet server service? This isn't my server that i'm connecting to.  Like i said i'm using the client in shell at the moment and i dont see any service to start.

---

### Post by steve.horsley on 2006-08-09
I can connect to it OK, so it is listening, although what comes back is unintelligible gibberish to me (and took several seconds to appear). 

There must be something dropping your packets. And if you can telnet other services on that address, then the filter is port specific. To be honest, I can only think of two possible things:

1) The service provider is blocking port 6000 from your IP adress but not mine for some reason
2) Your ISP is blocking port 6000 for some reason.

I suspect your ISP.

---

### Post by natan- on 2006-08-09
That jibbish is fine (its actually a game login server so telnet is just used to see if i can access it on that port).  It isn't an isp issue as i can actually telnet in from my router, just not from my computer behind the router. I found something interesting, if I do this:

grep '6000' /etc/services

I get:

x11             6000/tcp        x11-0           # X Window System
x11             6000/udp        x11-0

Would this cause my problem?

---

### Post by patrick295767 on 2006-08-09
> **natan- said:**
> I am trying to connect to a server using ubuntu. So I type this into the console:

telnet 216.98.58.100 6000

And I can't get through and I dont have any firewalls active that I know of just a router. You are welcome to try it out for yourself, you should get some jibberish text on connect.  How would I troubleshoot what is keeping me from connecting?

small info : 
(telnet is not secured 
ssh is highly recommanded)

---

### Post by natan- on 2006-08-09
ROFL and that reply is rediculous. The main reason why I will probably be formating back to xp in a week even tho it maybe unsecure and what not, but atleast i can do stuff on it and if there is a program blocking something I can find out pretty quickly.  Did you even read any of the posts in this thread?  I have this server. It isn't an SSH server it isn't a TELNET server its some propietary format protocol GAME LOGIN SERVER on PORT 6000.  NOW my problem is I can't log onto this LOGIN SERVER which ISN'T nessicarily a TELNET server.  I am mearly showing my problem utilizing a TELNET client. If I can't connect with TELNET, I can't connect via ANY MEANS. Why is this? I have no clue, I didn't come to get a lecture on the evil that is telnet, I came to find out why I spend 4 hours finding out why I can't use port 6000 but no one seems to have a clue.

---

### Post by steve.horsley on 2006-08-09
> **natan- said:**
> 

x11             6000/tcp        x11-0           # X Window System
x11             6000/udp        x11-0

Would this cause my problem?

I don't think so. Although 6000 is sometimes used for Xwindows, even if you had such a server running on your PC, it would not prevent your PC from calling to port 6000 on a different computer. Your PC calls **from** what is effectively a random port number, and all running a local Xserver woudl do would be to ensure that your local port 6000 was busy and could not be used for outging connections. But that doesn't stop your PC calling out from any other port number to port 6000 on your server. Hope that makes sense, but in short, this is not the problem.

P.S. Don't be too hard on Patrick. He's trying to help, and I suspect English is not his first language (location Belgium).

PPS. You aren't running a local firewall, I presume. Ethereal will show if the connect request (SYN) packets are leaving your PC.

---

