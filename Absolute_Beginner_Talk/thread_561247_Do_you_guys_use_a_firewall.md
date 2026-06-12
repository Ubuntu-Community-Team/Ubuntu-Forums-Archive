---
title: "Do you guys use a firewall?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-27
Hi people,
I was reading an article on LINUX Format (greek version) and it had some reviews on Linux Distributions. Ubuntu came first at the end, but looking at the security tests, it mentioned that Ubuntu does not come with a firewall.
Now I was wondering if we do actually need a firewall running?
Do people use one with Ubuntu?

I don't use one or virus protection software.

---

### Post by mcduck on 2007-09-27
No, you don't need a firewall with Ubuntu, as long as you don't install any server software on your machine. Ubuntu is safe even without a firewall as in the default setup there are no programs running that would respond to incoming connections.

---

### Post by w4ett on 2007-09-27
Ubuntu comes with iptables installed in the default installation.  The Firestarter gui frontend is a graphical control for iptables.....all ports are by default closed, unless you open them.

---

### Post by ROUBOS on 2007-09-27
that's good to know. Glad to see I'm safe with Ubuntu. 
So no need for anti-virus or anti-spam right?

---

### Post by mcduck on 2007-09-27
> **w4ett said:**
> Ubuntu comes with iptables installed in the default installation.  The Firestarter gui frontend is a graphical control for iptables.....all ports are by default closed, unless you open them.

Yes, but iptables alone is not a firewall. It contains all tools needed by firewalls, but it needs some program or script to actually set the firewall rules on boot.

And all ports are actually open by default. There's no need to close them as, like I said, there are no programs running that would respond to any incoming traffic on any port.

Edit: yes, no need for anti-virus or antispyware either. There is ni viruses for Linux running wild, and I haven't ever even heard of Linux spyware :D

---

### Post by ROUBOS on 2007-09-27
LOVE UBUNTU. Never gonna change again. Converted for good.
Feels great :)

---

### Post by santiagoward2000 on 2007-09-27
I do use Firestarter and ClamAV. I know they might not be necessary, but it's hard to get rid of my Windows paranoia...

---

### Post by ROUBOS on 2007-09-27
So the difference is that in Window$ there are open ports by default? I know that viruses and spam are written to hit window$ systems, but makes window$ so insecure ? IS it just badly written code?

---

### Post by madoracle on 2007-09-27
Since I setup an SSH server and a webserver on my Ubuntu box, I ended up going with a firewall. Specifically Firestarter since you can configure outbound and inbound rules.

---

### Post by Niniel on 2007-09-27
Since this is the absolute beginner section... with all ports open, won't that allow someone access to your machine? Send something to your computer and run it? Wouldn't a port scan light you up like a Christmas tree and invite "bad people" to try and hack you?
I mean, Nixes may not have viruses, but they do have bugs and there are exploits, and worms and trojans come from the Unix world, so why leave ports open by default?

---

### Post by madoracle on 2007-09-27
If you have a straight pipe from your ISP? Yes. But if you're behind a Wireless or Wired router and not directly coming from a pass thru (like most cable modems do) you're fine. Here's why:

Routers, 99% of the time, have a built in firewall. They allow outbound access and inbound if you initiate it from inside the network (ie logging onto an FTP server). But if Joe Hacker tries attacking you, he has to get thru the firewall on your router FIRST. This can be easy or difficult, depending on the router configuration. Things like allowing outside access to the configuration and not putting on a password would fall under 'making it easy'.

Now if you run a _server_ behind that firewall/router box, then you have to setup forwarding  for either specific ports OR put your linux machine in the DMZ. _Then_ you arae exposed to the world (either just the forwarded ports or your entire box, depending).

So basically, if you're running a server or if you have a cable modem and use nothing for a router/firewall - you need a software firewall. Otherwise, no.

Worms and trojans and such are another kettle of fish. Generally you recieve them from a website or from an email or the like, so a firewall will do nothing for you. Antivirus will.

---

### Post by mcduck on 2007-09-27
> **Niniel said:**
> Since this is the absolute beginner section... with all ports open, won't that allow someone access to your machine? Send something to your computer and run it? Wouldn't a port scan light you up like a Christmas tree and invite "bad people" to try and hack you?
I mean, Nixes may not have viruses, but they do have bugs and there are exploits, and worms and trojans come from the Unix world, so why leave ports open by default?

No. As long as nothing responds to incoming traffic on those open ports nobody can access the machine through them.

It's like if your boss calls your phone to tell that you need to do something, if you don't answer the phone hes not able to give you any commands. ;)

It's a bit different in Windows because by default it has services that respond to incoming connections, and because you cant actually trust that any of your software is not going to 'call home', so you need a firewall to restrict their access.

---

### Post by ROUBOS on 2007-09-27
OK cool
So looks like I'm OK with my Ubuntu box behind my US Robotics adsl router

---

### Post by Niniel on 2007-09-27
Ok, good.
Not that it seems to matter due to the absence of services accepting traffic, but most consumer-routers afaik don't have real firewalls built in but simply employ NAT. That's good enough I suppose?

---

### Post by bodhi.zazen on 2007-09-27
If you are interested in security, please see this thread :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

It has been designed (it has been reviewed by the mods and admins) to cover these issues.

---

### Post by Niniel on 2007-09-27
Nice, thank you, I shall most certainly read that.

---

