---
title: "Antivirus and Firewall"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-06-10
Is there any antivirus and firewall available in ubuntu 7.04 for security reason, i use my computer personally no other person use. If it  is avaialble how to install it. i am using ADSL modem to use internet

---

### Post by starcraft.man on 2007-06-10
> **ferronica said:**
> Is there any antivirus and firewall available in ubuntu 7.04 for security reason, i use my computer personally no other person use. If it  is avaialble how to install it. i am using ADSL modem to use internet

Ubuntu has a built in firewall already active called IPtables. Unless you have to port forward, leave it alone until you find a reason to modify it (If you need to open ports, download and use "firestarter" its in the repos). Ubuntu doesn't have a built in AV cuz it just doesn't need one.... the only reason an Ubuntu PC needs an AV is if you forward many email attachments to friends using windows, then download and install KlamAV. Otherwise, don't worry.

This [article is a good talk about security.]("http://www.psychocats.net/ubuntu/security")

---

### Post by ferronica on 2007-06-10
thanx starcraft.man for your reply :)

Can you please explain me what is port forwarding and what the use of port forwarding. can i increase download speed via port forwarding ????

---

### Post by diatribe on 2007-06-10
there are ways to increase torrent download speeds with port forwardng, just try google

---

### Post by Jimmyfj on 2007-06-10
> **ferronica said:**
> thanx starcraft.man for your reply :)

Can you please explain me what is port forwarding and what the use of port forwarding. can i increase download speed via port forwarding ????


Not that I know of. Port forwarding means that you redirect traffic from one port to another. Regarding AV in Ubuntu the only reason for installing antivirus software is if you're forwarding mails containing executable files from your Linux-computer to a Windows computer. To be nice, so to speak, you sleep better at night knowing that a friends computer didn't crash due to a virus send or forwarded from your computer.

---

### Post by starcraft.man on 2007-06-10
> **ferronica said:**
> thanx starcraft.man for your reply :)

Can you please explain me what is port forwarding and what the use of port forwarding. can i increase download speed via port forwarding ????

I'll just add to what Jimmy said regarding ports. Ports are how traffic (both network local and internet traffic) are managed and communicated from one machine to another (whether its a desktop or server from a website). There are ports for html for instance, for file sharing the list goes on... there are thousands and listing them all would be somewhat tedious, they are just the expected means for sending data for particular services to make it all organized.

There are 3 types of ports (or rather status) there is closed, open and stealthed. IPtables on Ubuntu has closed ports by default I believe, this makes it very secure, so if anyone tries to use the given port they will find out it is closed to their access. Open ports are just the opposite, they are freely available for access by anyone who is online. When you port forward you are essentially doing this by letting people connect to a particular port. This speeds up p2p because of technologies like DHT and peer exchange I believe. Stealthed ports are those that are closed and who do not appear on the internet. Where as closed ports will respond that they are closed, stealthed ports will not even respond. This IMO is the ultimately security, it makes you disappear from the net. 

I hope that gives ya a good general overview. I might have mixed/gotten a few things minorly wrong, I was writing fast. Download and listen to [episode 43 of this site]("http://www.grc.com/securitynow.htm") on open ports to understand more about them.

IMO, the best firewall anyone can get is a NAT enabled router, you put your internet behind it and your stealthed so long as your not port forwarding for p2p. Hope that helps, now have fun :).

---

### Post by steve.horsley on 2007-06-10
Another explanation of port forwarding...

An incoming connection to a server can connect to one of 65535 possible port numbers. Different services listen on different standard port numbers - HTTP on port 80, SSH on port 22 etc. A fuller list is found in /etc/services.

If you are behind a NAT router rather th\n directly connected to the internet, then (obviously) you have a different IP address to the publucly visible address on the router. Frinstance, your public address might be 1.2.3.4, but everything on your local LAN being 192.168.0.xxx. When you connect to someting on the internet, the router has to do network address translation, translating your address to the public address in every packet that passes (this may also involve having to translate port numbers too). So an outgoing connection sets up an entry in a translation table in the router saing that this address/port translates to that address/port.

The problem is that for incoming connection requests, the router doesn't know which internal address to translate to (there 254 possible addresses to forward the connection request to). So if you want incoming connections to be passed through to a particular internal address, you have to configure the router specifically to forward to the right machine. Since different internal machines can be running different services, you may want to forward connection requests to port 80 (HTTP) to your web server address, and port 25 (mail) to your mail server for instance. This is known as configuring port forwarding. Obviuosly it only applies when using a NAT device, and incoming calls cannot happen at all without it. 

If using Bit Torrent, it can improve download speeds to configure port forwarding so that other machines can connect to yours, although one would think that your being able to connect to other machines would be enough. But it does seem to make a difference. And think - of all machines could only make outgoing calls, peer-to-peer networks wouldn't work at all because there would be nothing for your outgoing calls to connect to.

---

### Post by notmicrosoft on 2007-10-02
You people are GREAT!!!
So although ,so far, the only people I connect to via e-mail are microsoft users, I won't have to worry about getting or giving a virus, bug, etc...?

---

### Post by bas1 on 2007-10-02
> **notmicrosoft said:**
> You people are GREAT!!!
So although ,so far, the only people I connect to via e-mail are microsoft users, I won't have to worry about getting or giving a virus, bug, etc...?

More than 99% of all viruses spread throughout the web are for microsoft windowz users, and a very, very, very, very, very, very, small # (I'm thinking less than a hundred?) of them are for any thing else, and a fraction of those viruses are for linux. In summary, you should not worry at all about getting a virus, only about spreading one. That is one of the big reasons for using linux. 

And while we are all talking about firewalls and security, I have a question. I would like to open up one of my ports for SSH, but I am afraid of hackers finding their way through and attacking my local network of computers (two running linux, one running xp). Is their anything I can do to protect my computers any further than having a NAT-enabled router & firewall?

---

### Post by psusi on 2007-10-02
Linux is not broken by design so there is no need for firewalls, antivirus, and all that crap you are used to from windows.  

As for ssh, you need not worry; nobody can get in unless they know your login and password.  If you really are paranoid, you can disable password logins and require the use of RSA keys.

---

### Post by shankhs on 2007-10-03
Ubuntu has inbuilt firewall.Does this mean that ubuntu cant be cracked by crackers??????
By just invading the ports and/or looking for opened ports????????:)

---

### Post by hyper_ch on 2007-10-03
Everything can be cracked... and in Linux it will mainly be due to people not respecting some basic principles like "do not run permanentaly as root", ...

---

### Post by psusi on 2007-10-03
> **shankhs said:**
> Ubuntu has inbuilt firewall.Does this mean that ubuntu cant be cracked by crackers??????
By just invading the ports and/or looking for opened ports????????:)

It is not that it has a built in firewall - it simply does not need one.  Firewalls exist only to protect broken servers.

---

