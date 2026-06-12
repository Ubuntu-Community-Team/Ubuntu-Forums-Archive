---
title: "Firewall"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jordanae on 2007-12-08
I am downloading WoW and it says "your computer appears to be behind a firewall".
How do I disable it?

---

### Post by taurus on 2007-12-08
You can install firestarter and use it to open a port for your game if you wish.  

```
sudo apt-get update
sudo apt-get install firestarter
```

---

### Post by muskratmx on 2007-12-08
If you don't have a firewall installed, you might have a modem/router with security settings to high.

---

### Post by thelatinist on 2007-12-08
> **muskratmx said:**
> If you don't have a firewall installed, you might have a modem/router with security settings to high.

Everyone running Ubuntu has a firewall called iptables which is set to block all incoming connections by default. Applications like Firestarter just act as a GUI for changing its settings.

---

### Post by muskratmx on 2007-12-09
> Everyone running Ubuntu has a firewall called iptables which is set to block all incoming connections by default. Applications like Firestarter just act as a GUI for changing its settings.

Everybody running LINUX has a firewall called iptables. The common term in English is miss used, I have had many discussions on this use of the term firewall with my dad, and others. The Linux kernel operates with perimeters from the iptables and acts as a firewall, But the public and programers both continue to propagate the term firewall as an addition package/program

But thier never set so high as to be unusable by default, Iptables can become unusable if  you mess with them via an editor or GUI firewall tool.

But I have seen router/modems that have had settings set to high by default.

---

### Post by The Cog on 2007-12-09
> **thelatinist said:**
> Everyone running Ubuntu has a firewall called iptables which is set to block all incoming connections by default. Applications like Firestarter just act as a GUI for changing its settings.

This is **[COLOR="DarkRed"]wrong[/COLOR]**. 
A default Ubuntu install does not have any blocking firewall rules running. The default is to permit everything.

---

### Post by Kosimo on 2007-12-09
I'm very interested on it....

Can please someone make this a bit more clear?  Do we have any kind of protection in a default Ubuntu Installation? (gutsy)

---

### Post by Kosimo on 2007-12-09
> **Kosimo said:**
> I'm very interested on it....

Can please someone make this a bit more clear?  Do we have any kind of protection in a default Ubuntu Installation? (gutsy)

By the way... Do we really need it?

---

### Post by p252 on 2007-12-09
This topic is the subject of much debate on this forum and in the end really boils down to point of view. While I do wish that Ubuntu would include an easy to use firewall configuration program (other than the, from what I can tell, unmaintained Firestarter), Ubuntu is inherently safe by default. On a fresh install of Ubuntu, Iptables has no rules defined, all incoming and outgoing traffic is accepted (run 'sudo iptables -L -v' to see that there are no rules defined). This is safe because, on a fresh install, Ubuntu has no programs installed that is listening for inbound connections. What is the point of blocking all inbound requests if the system is not running any programs that would respond to requests? Where one might want to start running a firewall is if server software starts getting installed (e.g. samba server, nfs server, ftp server, etc.) Even then, unless you want to limit allowed incoming traffic to specific IP subnets, you may not want to install a firewall, since, if running a server with open ports, you would probably have opened those specified ports in the firewall anyway. For example, after a fresh install of Ubuntu I install samba server which listens to specific incoming connections. Being that it's a server I have maintained, I know that samba is the only program installed listening to connections and I regularly port scan that server to make sure those are the only ports open. This would be the same setting up firewall rules that allow the specific samba ports in, either way, the ports are open for incoming connections.

---

### Post by p252 on 2007-12-09
jordanae, if you are running a high speed internet connection with a router, the firewall very well may be in the router. You may want to check the settings of your router and open the specific ports you need in there.

---

### Post by thelatinist on 2007-12-09
> **The Cog said:**
> This is **[COLOR="DarkRed"]wrong[/COLOR]**. 
A default Ubuntu install does not have any blocking firewall rules running. The default is to permit everything.

I stand corrected.  Ubuntu's default settings are not to block incoming connections.  Of course no software in a default installation is listening for incoming connections, so you are still safe.  If you install any kind of server software that you don't trust to respond only as you want, you could always use Firestarter to close ports.

---

### Post by fmartinez on 2007-12-09
> **The Cog said:**
> This is **[COLOR="DarkRed"]wrong[/COLOR]**. 
A default Ubuntu install does not have any blocking firewall rules running. The default is to permit everything.

Actually from my understanding a standard installation of linux by nature is start with everything closed (ports), unless otherwise specified. This is what ads to Linux security.

---

### Post by muskratmx on 2007-12-10
> Actually from my understanding a standard installation of linux by nature is start with everything closed (ports), unless otherwise specified. This is what ads to Linux security.

No that's not true. Almost all linux desktop installs with CUPS, are listening with an open port for the printer. There is some that install closed. I have several installs that have an FTP port listening after the install.

So if you don't have a great understanding of iptables, such as my self. Firewall GUIs like firestarter are a great plus for us.

---

### Post by pfeels on 2007-12-10
Ok, I'm like millions before me and new to this world, I have a Linksys G, I imagine it has a router so I don't have to worry about setting up one with Ubnutu, is that right or wrong, or is it not a simple answer? ... I'm using Thunderbird for email ...

Also I read that anti-virus is not needed, is that to good to be true?

---

### Post by muskratmx on 2007-12-15
> I have a Linksys G, I imagine it has a router so I don't have to worry about setting up one with Ubnutu, is that right or wrong, or is it not a simple answer? ... I'm using Thunderbird for email ...

Also I read that anti-virus is not needed, is that to good to be true?

I'm not familiar with Linksys G, But all cable modems/routers can be accessed via the web browser. You'll need the IP number, with that you access the control panel in the router and see just what the settings are. I modem won't have any firewall blocking abilities. A router generally does. Just how much depends on the system. And whether or not there their sufficient depends on your paranoia level.

As for anti-virus, their are a few viruses for Linux, but not many and most desktops won't ever be exposed to them. But you can have virus infect files on your system. When you copy them to media and then access then with a windows machine, it becomes infected. Or if you email them to a MS using friend.

One of the worst is when you receive a email, then forward it to a friend. It's infected, and you never know because it couldn't infect your box, but your friend gets nailed. Now you lost a friend, because you didn't have an anti-virus program.

---

