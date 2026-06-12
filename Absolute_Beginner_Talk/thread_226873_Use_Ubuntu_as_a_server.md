---
title: "Use Ubuntu as a server?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-07-31
How good is Ubuntu Linux for use as a server?

---

### Post by Captain Kirk76 on 2006-07-31
bump

---

### Post by Captain Kirk76 on 2006-07-31
bump

---

### Post by T700 on 2006-07-31
It's fine.

Paul

---

### Post by benplaut on 2006-07-31
depends on what kind of server you want.  For a fileserver, musicserver, whatever, it doens't really matter what distro you use.  All can do it, and it's not really a highly complcicated process.

For a LAMP webserver, i recommend debian.  It's stable as a rock.

---

### Post by Captain Kirk76 on 2006-07-31
Its only gonna be used to host a foorum, not too taxing....
Would Ubuntu be stable enough for that?

---

### Post by IYY on 2006-07-31
Yes, it would be perfectly stable. If it was me making the decision, I'd still go with Debian just to be sure (Ubuntu's main strengths are in the desktop market, and it's pretty much the same as Debian as a server).

---

### Post by T700 on 2006-07-31
> **Captain Kirk76 said:**
> Its only gonna be used to host a foorum, not too taxing....

Hmm...you might want to check with folks who run this one about that!

Three things to keep in mind.  First, a server is a huge, red flag, bullseye target, on the net.  You've got to keep security foremost or you *will* be owned.  Second, make sure you are fluent and comfortable with the command line, as the Ubuntu server install does not have a GUI (as is the same for the majority of servers in the Linux/UNIX world).  Third, see the first one again--it's that important.

Good luck,
Paul

---

### Post by verbatim210 on 2006-07-31
iyy, benplaut.  
are you guys preferring debian over ubuntu as a server? (in general)

please go into detail :D

---

### Post by Captain Kirk76 on 2006-07-31
Currently im having trouble getting APACHE To listen to the right ports, and im still trying to determine if my ISP isblocking ports 21, 21, 25, or 80.

Also, Does Ubuntu allow Remote access, so if i went away, my co-admin could use remote access to maintain it?

---

### Post by IYY on 2006-07-31
I'd actually use FreeBSD or NetBSD as a server. They tend to be a bit more secure.

---

### Post by T700 on 2006-07-31
> **Captain Kirk76 said:**
> Currently im having trouble getting APACHE To listen to the right ports, and im still trying to determine if my ISP isblocking ports 21, 21, 25, or 80.

Also, Does Ubuntu allow Remote access, so if i went away, my co-admin could use remote access to maintain it?

If they are blocking, you can use one of the service such as No-IP to redirect around it.  

Yes, you can allow remote access, but at the risk of sounding like a nag, you've got to be **really** careful with that or it is just a "welcome hackers" sign hung out on the net.

Paul

---

### Post by verbatim210 on 2006-07-31
ssh for the remote access question
[http://localhost/](http://localhost/) for the isp blocking port question

---

### Post by verbatim210 on 2006-07-31
i've had a lot of trouble installing freebsd in the past concerning my disc geometry

yet to give netbsd a try, any particular differences?

---

### Post by Captain Kirk76 on 2006-07-31
Hold on, If my ISP Blocks port 80 (the one used for HTTP Requests) i cant host a server, is there a method of getting around this, (that works)

---

### Post by T700 on 2006-07-31
> **Captain Kirk76 said:**
> Hold on, If my ISP Blocks port 80 (the one used for HTTP Requests) i cant host a server, is there a method of getting around this, (that works)

"If they are blocking, you can use one of the service such as No-IP to redirect around it.  "

Paul

---

### Post by Captain Kirk76 on 2006-07-31
I read that thanks, but i dont understand how it works. I thought if an ISP Had blocked it that was it, tough tits.

---

### Post by T700 on 2006-07-31
> **Captain Kirk76 said:**
> I read that thanks, but i dont understand how it works. I thought if an ISP Had blocked it that was it, tough tits.

Not at all.  Check out [this free service]("http://www.no-ip.com/") that allows you to easily circumvent that.  I do it for several servers and more than a dozen desktops (for remote access with DHCP).

Paul

---

### Post by Captain Kirk76 on 2006-07-31
Perfect, i should have my Ubuntu running as a server in no time :p 
Thanks alot!

---

### Post by gregben on 2006-08-01
> **Captain Kirk76 said:**
> Currently im having trouble getting APACHE To listen to the right ports, and im still trying to determine if my ISP isblocking ports 21, 21, 25, or 80.

Also, Does Ubuntu allow Remote access, so if i went away, my co-admin could use remote access to maintain it?
Remote access to virtually any *nix system (Ubuntu included) is done through ssh (secure shell).
The server needs to run 'sshd', the ssh server daemon.

---

### Post by meney on 2006-08-01
> **Captain Kirk76 said:**
> Hold on, If my ISP Blocks port 80 (the one used for HTTP Requests) i cant host a server, is there a method of getting around this, (that works)

If your ISP is blocking port 80, there is probably a good reason for it (such as your contract explicitly stating no web hosting ;) ). Your also probably going to want a static IP address, it could get hectic with a dynamic one. All in all, I would contact your ISP to see what their rules are, and if it will cost more for a static address.

Regards,

---

### Post by Captain Kirk76 on 2006-08-01
apparantly static IPs are £5 per month (about $10) from my ISP.
How hard would it be from a Dynamic IP

---

### Post by Captain Kirk76 on 2006-08-01
Bump. I really need the last question answering.

---

### Post by az on 2006-08-01
Servers for beginners:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

DynamicDns:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

Hosting forums:
[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)
[https://help.ubuntu.com/community/PunBB](https://help.ubuntu.com/community/PunBB)

---

### Post by jrjr on 2006-08-01
.

---

