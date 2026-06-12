---
title: "Troubleshooting Internet Connectivity"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Onos on 2006-02-01
Trying to figure out what the (Ubuntu) Linux equivalents of certain Windows line commands...

my internet seems to be particularly sluggish recently, and even after a service call to the cable company, it is only marginally faster: firefox chuggs along for a good 5 minutes after loading a site, with hotmail and blogger proving to be especially slow (I am talking sub-dialup speeds) and often triggering a "server reset by peer" or simliar errors.

On a Windows box, I know I can do the following:

**ipconfig** (release and renew the DHCP and flush/register DNS)

**ping** 

**tracert** (trace the route to a specificed IP)

what would be useful linux commands to try and feel out what is going on through my network card?

---

### Post by o_fortuna on 2006-02-02
[QUOTE=Onos]Trying to figure out what the (Ubuntu) Linux equivalents of certain Windows line commands...

my internet seems to be particularly sluggish recently, and even after a service call to the cable company, it is only marginally faster: firefox chuggs along for a good 5 minutes after loading a site, with hotmail and blogger proving to be especially slow (I am talking sub-dialup speeds) and often triggering a "server reset by peer" or simliar errors.

On a Windows box, I know I can do the following:

**ipconfig** (release and renew the DHCP and flush/register DNS)

**ping** 

**tracert** (trace the route to a specificed IP)

what would be useful linux commands to try and feel out what is going on through my network card?[/QUOTE]
In Applications-->System Tools-->Network Tools you'll find some useful options, including ping and traceroute. Also, **ping** is the only one of those that works on the command line. I don't know the equivalent for **tracert** on the command line, but for **ipconfig**, if you want to deactivate a network interface, just type
```
sudo ifdown <interface>
```
and to activate one type
```
sudo ifup <interface>
```
A few other commands you might find useful:
iwconfig - show wireless information
ifconfig  - show network hardware/IP information
ip         - configure the network

[This]("http://www.tldp.org/LDP/intro-linux/html/sect_10_01.html") might be useful.

I'm probably missing some others, but it's been awhile since I've had to reconfigure my network.

EDIT: If you don't know what a command does, type "man <command>" at the terminal. That will show you the manual; it's very useful when getting used to the terminal.

---

### Post by Dominus Suus on 2006-05-20
The GNU equivalent to tracert is... surprise surprise... traceroute.  You may have to sudo apt-get install traceroute manually, though, since I don't think it comes in the default install.

---

### Post by Pablo928 on 2006-06-15
Thanks, Dominus Suus! I've been trying to use traceroute with a command line to no avail. (Works so much better with traceroute installed.)

---

