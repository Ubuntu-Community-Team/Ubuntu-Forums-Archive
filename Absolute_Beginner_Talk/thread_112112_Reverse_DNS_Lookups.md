---
title: "Reverse DNS Lookups"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Fatjoint on 2006-01-03
I am new to Ubuntu and am having a problem with trying to figure out what program to use in order to do reverse dns in a classless(?) network.

I have tried using **dig** and **host** but can't seem to get things right.

I am taking an IP address such as 10.200.10.17 and trying to query the DNS server as to what the hostname of that PC is.  Everytime I do this, I have the following output.

> 
Host 17.10.200.10.in-addr.arpa not found: 3(NXDOMAIN)


Now what I'm guessing is that **host** is going out and trying to resolve that IP at the root servers of the internet.  So I read the **man** pages and try to figure out how to point it at our internal DNS server.  I come across this in man

> 
SYNOPSIS
       host [ -aCdlnrTwv ]  [ -c class ]  [ -N ndots ]  [ -R number ]  [ -t type ]  [ -W wait ]  [ -4 ]  [ -6 ]  name
       [ server ]

DESCRIPTION
**host** is a simple utility for performing DNS lookups.  It is normally used to convert names to IP addresses and vice versa.  When no arguments or options are given, host prints a short summary of its command line arguments and options.

**name** is the domain name that is to be looked up. It can also be a dotted-decimal  IPv4  address  or  a  colon-delimited  IPv6 address, in which case host will by default perform a reverse lookup for that address.  server is an optional argument which is either the name or IP address of the name server that  host  should  query instead of the server or servers listed in /etc/resolv.conf.


So it seems relatively easy, that I should be able to type in something like:

host 10.200.10.17 10.200.100.100

argument 1 being the IP address of the machine I'm trying to resolve the name for and argument 2 being the IP address of our internal DNS server.  I always get this when I type this however, which is not the same as the first output that I got, but equally as frustrating.

> 
Using domain server:
Name: 10.200.100.100
Address: 10.200.100.100#53
Aliases:

Host 17.10.200.10.in-addr.arpa not found: 3(NXDOMAIN)




Can anyone help me on this?

---

### Post by Sheco on 2006-01-03
nslookup?

---

### Post by ape on 2006-01-04
This looks to be something with your internal DNS server as I'm able to use the host command to do a reverse lookup of my firewall's external address successfully.

Can you successfully do a reverse lookup on a publicly available server ([www.ubuntuforums.org?](www.ubuntuforums.org?))

Here's what I get:

 First, get the IP address for [www.ubuntuforums.org:](www.ubuntuforums.org:)
 
[FONT="Courier New"]host [www.ubuntuforums.org](www.ubuntuforums.org)
[www.ubuntuforums.org](www.ubuntuforums.org) has address 64.21.33.9[/FONT]


 Now do the reverse:

[FONT="Courier New"]host 64.21.33.9
9.33.21.64.in-addr.arpa domain name pointer wailuku.xlogicgroup.com.[/FONT]

---

