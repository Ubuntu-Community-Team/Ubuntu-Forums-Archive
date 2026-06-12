---
title: "So, let me get this straight..."
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by chrispche on 2008-01-04
You don't need to install Firestarter as there is a firewall in operation by default? You don't need ClamAV's frontend as it does everything in the background, updating via freshclam ect.

But you can install GUI versions of these if you so wish? What for? To change settings of the deamons running?

---

### Post by LaRoza on 2008-01-04
If you are not a server, or an email server (or doing Windows file shares) you don't need any of that.

iptables leaves no ports open, and a router is the only firewall you need. ClamAV is not installed, but you can install it if you want to scan email attachments and such or if you deal with Windows file sharing a lot.

---

### Post by ukripper on 2008-01-04
To intercept virus for windows box or potential hack!

---

### Post by philinux on 2008-01-04
I had this "windows" mind set when I went ubuntu in July last year. When I did the gutsy install I just left iptables to do its thing, no virus checker installed either. 

I have a router with its firewall and I only use my hotmail account to register with websites. 

I've had no adware, no virus alerts, no spam. **No more** spybot, adaware, zonealarm, regclean, etc etc.

 **Magic**

---

### Post by hyper_ch on 2008-01-04
> **LaRoza said:**
> iptables leaves no ports open
Actually as far as I understand it ports are open by default (not closed) but there's no services listening to them.

---

### Post by ukripper on 2008-01-04
If you do alot of banking online i would recommend you have firefox addon called noscript. It stops any script running behind the scene while you enter your details. [https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

it is a top notch script blocker

---

### Post by LaRoza on 2008-01-04
> **ukripper said:**
> If you do alot of banking online i would recommend you have firefox addon called noscript. It stops any script running behind the scene while you enter your details. [https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

it is a top notch script blocker

Most scripting exploits come from IE flaws.

If you do use it, which I endorse, be sure to allow sites you trust to run scripts.

---

### Post by philinux on 2008-01-04
> **hyper_ch said:**
> Actually as far as I understand it ports are open by default (not closed) but there's no services listening to them.

Hey this is interesting. I've heard both, no ports open and all ports open so i had to delve.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

> When you install Ubuntu, iptables is there, but it allows all traffic by default.

Now does that mean ports open or are opened to allow traffic as needed eg browser deluge etc.

---

### Post by jonnywombat on 2008-01-04
If you want to see what ports you have open and closed then visit the shields up site at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) 

I find that from behind a router a default install of ubuntu passes all test and all ports are in "stealth mode" :guitar:

Jonny

---

### Post by philinux on 2008-01-04
> **jonnywombat said:**
> If you want to see what ports you have open and closed then visit the shields up site at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) 

I find that from behind a router a default install of ubuntu passes all test and all ports are in "stealth mode" :guitar:

Jonny

Yep did this test and full stealth. But thats the router not iptables or ubuntu correct?

---

### Post by benny bronx on 2008-01-04
shields up  may be testing your router, not your comp.  I heard that all ports are closed by default because no services are listening.  Does someone have a definitive answer.

---

### Post by stump138 on 2008-01-04
Shields up will definitely be testing your router/firewall and not the local machine.  There may be exceptions if you are using NAT.

I use NMAP for port scans.  There is a gui front end you can get as well
```
sudo apt-get update && sudo apt-get install nmap nmapfe
```

Tons of options and there are tutorials available with a quick search

---

### Post by ukripper on 2008-01-04
> **LaRoza said:**
> Most scripting exploits come from IE flaws.

If you do use it, which I endorse, be sure to allow sites you trust to run scripts.

i only do trust on ubuntuforums. Rest i have no trust except my own webserver hosting site

---

### Post by Yoke &amp; Chung on 2008-01-04
> **philinux said:**
> Yep did this test and full stealth. But thats the router not iptables or ubuntu correct?

If you are running behind the router, yes, your router is blocking the Shieldup. If you want to test iptables, you can set your computer in the DMZ, this way, the NAT router will not block any traffic to your computer.

Correct me if I am wrong, I am a newbie to Linux too, as far as I understand from what I read, Firestarter is just a front end tool to allow you to configure iptables. I have run Azureus without Firestarter, and no traffic is allowed to connect to my "server" if I did not set explicitly to open the ports. (BTW, the computer is in DMZ, so no protection from router.)

Best Regards

---

### Post by The Cog on 2008-01-04
There are several parts to this. 

Firstly, about firewalls:
Linux has firewalling **capability** built in. It is configured with the command-line program called iptables. By default, the firewall has no rules other than a default policy that allows everything. You can see this with the command **iptables -L** which will give this result:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
This means that by default, you have no firewall rules and your machine is open to the world. if you want to block anything, you must somehow issue commands to iptables to make the changes you want.

iptables can be configured by hand if you really know your stuff. To save doing this every time you boot, you can create a script that runs when you boot and issues all the commands.

GUIs like firestarter and guarddog make configuring iptables easier. The GUI collects your information, and then (behind the scenes) creates that script with all the iptables commands for you.

Secondly, about open ports:
An operating system has ports in one of two states:
Closed: This is the default - incoming connections are refused because no application is listening for connections on that port number.
Open: The operating system will accept connections to that port number, and pass those connectons to the listening application (print spooler, web server, whatever).

The firewall (if so configured) may of course discard packets to/from certain ports, in which case a caller will neither get accepted or rejected messages. Some people call this stealthed.

Thirdly, about the loopback address:
When an application wants to listen for incoming connections, it will normally ask to listen for incoming connections to any address on the machine. This is shown in netstat as address * or 0.0.0.0. However, every machine has a "loopback" address of 127.0.0.1 "localhost" which can not send or receive packets from the network. If an application decides to listen on only address 127.0.0.1 then it can only be connected to by other applications running on the same machine.

So is Ubuntu safe by default? Well, the firewall is effectively disables because it has a policy to allow everything. But most of the applications that you see listening (use the command **sudo netstat -plantu**)  are listening on 127.0.0.1 so they are only accessible from other processes on the same PC. In fact, the only things that are listening on 0.0.0.0 are avahi-daemon and dhclient. Both these are listening on UDP, not TCP, so a normal TCP scan will show all ports closed. But they are listening, and you have to decide if you feel safe with whatever they are exposed to packets from the Internet. 

I don't know that avahi-daemon is, but you can disable the service if you want (I do) with no apparent ill effects. I am unhappy that Ubuntu enables this service by default - its getting like windows in that you have to find and disable unwanted services to improve security. It's open by default and it just might have a bug that makes it exploitable.

dhclient is the DHCP client that asks a DHCP server for an IP address during boot-up. Why on earth it keeps listening for packets after that s a mystery to me.  Could it be used as a way to attack the machine? Possibly - I don't know. It may be worth configuring a firewall just to protect it and be safe. But it is probably safe to connect to the internet without firewalling. And many people do.

You can configure iptables to block all incoming connections but allow outgoing ones with these commands:
```
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -P INPUT DROP
```

If you decide to run a service of some sort, like a web or mail server, you just might want to use a firewall to prevent acces except from selected IP addresses. But web and mail servers are generally avai;able to the general public, which means a firewall is of no use. I actually run an SSH service at home, and have a firewall that only allows SSH connections from where I work - I don't want the rest of the world guessing passwords all day (and they do, or did before I turned the firewall on).

Another possible reason for running a firewall is to prevent most outgoing connections, and only allow selected protocols like HTTP. Why? In case your PC gets infeccted with something and tried to phone home, I suppose. Except that in my opinion, phoning home is likely to be done using HTTP anyway, and if you have been compromised then it's Game Over anyway, so I really don't see this as a good reason. 

Overall, I think running a firewall on a default Ubuntu install is more effort than it's worth, although Ubuntu security is deteriorating - early versions didn't have avahi-daemon listening by default, and I don't remember the DHCP client holding on to an open port. But if you install services yourself, you should think whether you want a firewall to keep the unwashed masses away from it.

Incidentally, most services can be configured with who they are allowed to talk to - the SSH service for instance can be configured only to allow specific users from specific addresses, and also consults hosts.allow and hosts.deny which are whitelist and blacklist files, so you may not need a firewall even if you do want to install a semi-private service. But I have to admit that configuring a firewall can be easier than finding the different ways of configuring access in a different way for a multitude of different services with different configuration files and formats and options.

UPDATE:
It occurs to me that the expression "open a port" can mean two differrent things. Firstly in the context of firewall configuration, it can mean configuring a firewall to allow packets to/from a particular port to pass unhindered. People often call this opening a port although "unblocking" a port might be a less ambiguous term as it has no effect on whether a port is seen as open or closed, it just affects whether the port can be seen (get some kind of response) at all. Secondly in the context of a computer operating system, opening a port is something that a service application like a web, mail, VNC, SSH etc. server does by telling the OS that it wants to listen for packets/connections on a particular port number. This transitions the port from the closed state (where a caller would be given a Port Unreachable message by the OS) to an open state where packets (UDP) or connections (TCP) are accepted by the OS and passed to the listening service application.

---

### Post by philinux on 2008-01-04
Good stuff. Good explanation I think. I'll have to read it again though. :lolflag:

---

### Post by CatKiller on 2008-01-04
> **The Cog said:**
> I don't know that avahi-daemon is, but you can disable the service if you want (I do) with no apparent ill effects. I am unhappy that Ubuntu enables this service by default - its getting like windows in that you have to find and disable unwanted services to improve security. It's open by default and it just might have a bug that makes it exploitable.

dhclient is the DHCP client that asks a DHCP server for an IP address during boot-up. Why on earth it keeps listening for packets after that s a mystery to me.  Could it be used as a way to attack the machine? Possibly - I don't know. It may be worth configuring a firewall just to protect it and be safe. But it is probably safe to connect to the internet without firewalling. And many people do.

avahi-daemon is for DNS. dhclient needs to check if any DHCP leases have been released,  and renew them as appropriate.

It's because of the inclusion of demons like these that a lot of the hot-plug configuration works automatically.

---

