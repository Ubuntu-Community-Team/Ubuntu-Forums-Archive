---
title: "Understanding ports and Firestarter"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by HeyItsMatt on 2007-03-29
Hey everyone.  I have some general questions about ports / services / firewalling, and some specific ones about firewalls for Ubuntu.

The first thing I'm wondering is what it means to open a port.  I keep trying to find information on the internet about networking but it's either the same basic stuff or something I can't understand at all.  When I open a port, is that a security risk in itself, or is it only a problem if I have a program set up to listen on that specific port?  I.E. can someone use one of my open ports for some negative purpose, or is it only dangerous if I have some exploitable program on my computer that is using that port to accept connections?

Secondly (here's a Firestarter-specific question), is there any way that I can just allow a particular program to make whatever connections it needs to make to function?  I have ZoneAlarm in mind on Windows, where you can set access rules for a program as opposed to opening ports.  It seems to me like this would work better and be safer, since the port would be open only as long as the program needs it (perhaps I am wrong, I am definitely not a networking expert).  If Firestarter cannot do this, is there some other firewall in roughly the same ease-of-use range that can?

Third, I have a port open in inbound connections of Firestarter for the service BitTorrent, but it's not in the normal 6881-6889 range (I'm using KTorrent's default port 65501).  This seems to make things work, except all the active connections in my 'status' tab for that port say the service is 'unknown' instead of BitTorrent.  I know that's probably just nitpicking, but I'm wondering why that is?  If I specify that incoming connections are for the service BitTorrent, then the port cannot be used for anything else, right?

Last, I have outbound connections set to "restrictive by default" and have some basic services I use allowed through certain ports.  When I start a torrent on KTorrent, I get a flood of connections of what looks like my computer trying to connect to other computers through various ports.  This doesn't seem to interfere much, though - after a bit of a slow start my torrent gets a decent upload/download rate.  Despite this, I'm wondering if it's best to open up a big port range for BitTorrent service in outbound connections?

Sorry if this is an excessive amount of questions, I'm just trying to understand a little more about this stuff, especially since I am planning to try to set up a webserver soon.  I feel like the more I try to learn about networking, the less I understand it, and I have a hard time finding any sites that are helpful to me.

---

### Post by renzokuken on 2007-03-29
this may be less detailed than you wanted but i'll give a go at a couple of your questions.

I imagine firewalls and ports as a really really REALLY long wall (the firewall) around your computer with over 65000 doors (ports) on it. now certain programs and services (torrent, ftp, http etc) need to travel through your wall to get access to the outside world, or alternatively, to let stuff into your computer.

it is usual that each service will be limited to using a specific door each time it needs to send/recieve info. now if the door is locked then no data can get through. here there are two options.

1. fully open the port  -  like just unlocking a necessary door and leaving it wide open all the time

2. uPnP  -  like keeping the door locked but giving the program the key to open the door so the door is only open when it needs to be.

you can specify which door you want each program to use and is best to give each program its own door.

leaving the doors wide open (option 1.)  is a security risk yes and uPnP is probably safer but at the end of the day, are we really safe?

hope this isnt too basic but its how i imagine it.

---

### Post by mcduck on 2007-03-29
Open ports are not a security risk unless there is some application listening for network traffic from that port.

If you have installed Firestarter it configures your firewall so that outgoing traffic is allowed from all ports, but incoming is blocked ulsess it's a respond to something you asked, for example when your web browser asks for some web page the incoming data is allowed. But for bittorrent and many most other P2P applications you need to allow the incoming traffic also when it's not a reply to something you did, and this is why you need to open the port to both directions.

---

### Post by denver on 2007-03-29
1. Think of a port as a door to your computer. By default in ubuntu all ports are closed. There are NO open doors through witch someone can access your computer. A port gets opened when a certain application sends a request to your kernel to open one. This happens when you need to start a public service ( Apache/FTP or any other kind of server that accepts connections on one or more ports ). Usually you can customize the port on which an application listens for connection and you can always find out which application listens on which port by typing
```
netstat -taupn
```
The only danger to you is if the application listening on a certain port is vulnerable and can be exploited to gain access to your computer. Otherwise that application only does what its supposed to do ( accept connections and respond to users requests, I.E. serve a web page --> apache ). Usually daemons( public services ) listening on certain port run under a separate user ( limited user usualy ) that doesent have access to any system critical configuration files. So even if that application gets exploited the hacker is limited to what the user under wich the application is running can do. Say you decide to start a daemon as your user. Your user has write access to /home/<user> and /tmp. So even if your user gets hacked, it only affects the files and folders owned by you.


2. Firestarter is a front end for iptables wich is in turn a front end for netfilter, a kernel module that deals with packet filtering at the kernel level ( the linux firewall ). iptables can block or reject specific packets based on source IP, destination IP, Source Port, Destination Port. It deals with ports, IP's and sometimes MAC addresses. You dont really need more then that on the count that viruses for linux are practically inexistent and you always need administrative rights to install an application. So blocking applications from your computer from accessing the internet is as easy as closing them all together. You should be more concerned with traffic coming FROM the Internet. That can easily be monitored using Firestarter. Any traffic coming from the Internet TO your computer can be handled and filtered by Firestarter based on the rules you give it. Lets say that you checked the /var/log/auth_log and found that IP address 192.168.0.5 tried to gain access by brute forcing his/her way in via ssh. You can create a rule in firestarter to block all acces from IP addres 192.168.0.5 to port 22....or to any port for that matter in which case the attacker wont have access to your computer at all. There are also a lot more programs/scripts that parse your logs for failed authentications and block the source IP automaticaly.

3. Most common port range from 1 to 1024. These are sometimes referred to as privileged ports. In this range are all the servers ( Web, FTP, DNS, etc ). Anything above these ports are non standard ports specific to one application or another. Thats why there appears to be an "unknown" application listening on that port. When you PERMIT for connections to come in to a certain port that means that in the event that one application or another requests that port to be opened in order to accept connections ( you start apache for instance ), the packets coming in to that port will not be rejected or dropped. If an application is already bound to that port, then it is impossible for another application to be bound to the same port. ( I.E. you start a game server on port 21. If you try to start a FTP server on the same port, it will complain that it cannot bind to that port because its taken by another application )

4. the torrent protocol is like a big spider web. There is a tracker that keeps count of each and every host sharing a certain file or files. When you attempt to download that file, you interrogate the tracker to find out who is out there and how much of the file each of them has. At this moment your client connects to as many hosts on that torrent as possible. The more people sharing the same thing, the better. The torrent protocol is designed to enable you to share a file with other people without consuming all your bandwidth. So all those outbound connections are normal to have. You can also limit them if you want by browsing your clients settings. Most of the torrent clients out there permit limiting of outbound connections.

I hope this helps you out a bit. I don't know if i explained things clearly enough but i hope i managed to clear things up a bit.

---

### Post by HeyItsMatt on 2007-03-29
Hey, thanks for all your answers guys -  they were a big help.

> **denver said:**
> The only danger to you is if the application listening on a certain port is vulnerable and can be exploited to gain access to your computer. Otherwise that application only does what its supposed to do ( accept connections and respond to users requests, I.E. serve a web page --> apache ).

Thanks, that definitely clears up some of my confusion about how ports work.  I was worried that somehow having an 'open' port would mean that something could come through and/or some 'open' program on my comp could be accessed even if it wasn't really related to that port.

> **denver said:**
> You should be more concerned with traffic coming FROM the Internet. That can easily be monitored using Firestarter. Any traffic coming from the Internet TO your computer can be handled and filtered by Firestarter based on the rules you give it. Lets say that you checked the /var/log/auth_log and found that IP address 192.168.0.5 tried to gain access by brute forcing his/her way in via ssh. You can create a rule in firestarter to block all acces from IP addres 192.168.0.5 to port 22....or to any port for that matter in which case the attacker wont have access to your computer at all.

Yeah, I have inbound connections from the internet blocked by default, except for one BitTorrent port for KTorrent to use, and an IP address or two for computers on my LAN.  I'm also behind a router, so I'm sure that the Windows partition on this computer is much more of a security risk than anything else - but I figured restricting outbound connections couldn't hurt as long as I could still use the programs I wanted to use.

Also, about blocking an outside IP address from accessing a port - I thought that Firestarter basically blocked all incoming connections automatically, unless you initiated a connection yourself and/or added an access rule to the policy tab?

Once again, thanks for your answers, they definitely helped clear things up a bit for me.  Despite some of the issues I've been having as a newbie, it sure is nice to have Ubuntu working well enough that I can stop getting asked if I want Windows to install Genuine Spyware on my system :)

---

