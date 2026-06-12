---
title: "DNS and slow internet"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Envy on 2006-06-15
So, I've been browsing trying to figure out the problems with my 'net connection

and I disabled my ipv6 - that didn't help

so I looked in [this thread]("http://www.ubuntuforums.org/showthread.php?t=157577&highlight=slow+internet+dns") and he talked about /etc/reslove.conf

or maybe he meant /resolve.conf

but I tried both and neither has anyithing at all in it!

so what info shuld be there? I suspect it's part of why I'm having problems

---

### Post by Garyu on 2006-06-16
I really don't know, but my /etc/resolv.conf looks like this:

```
search MSHOME
nameserver 172.16.3.3

```

So I guess you need your domain name and your DNS server? =)

PS. you didn't spell that file-name right... maybe that is your problem? check it out and make sure you typed /etc/resolv.conf (without the "e")

---

### Post by Data Doctor on 2007-08-10
I found a solution:

 Ubuntu is having difficulty with DNS because of miscommunication with your router (related to wrong ports).

  Establishing a direct DNS connection solves the problem. No need to disable IPv6!

1. Find your DNS servers. You may need to check your router settings (usually 192,168.1.1 or 192.168.0.1). Look for a status tab, or similar with the current DNS information. Write down your DNS servers (x.x.x.x & x.x.x.x).

You may wish to back up your dhclient.conf file at this point. In the Terminal, type:
cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.bak

2. Enter these DNS servers directly in your dhclient.conf file:

sudo gedit /etc/dhcp3/dhclient.conf

You should see your dhclient.conf file displayed (with text in it). Add two lines to the end:

supersede domain-name-servers x.x.x.x,x.x.x.x;
    prepend domain-name-servers x.x.x.x,x.x.x.x;

The x's represent your DNS server IP addresses that you found in Step 1.

Save your dhclient.conf file, close gedit and return to the Terminal.

Now restart your DNS lookup with (assuming eth0 is your connection to the router):

sudo ifdown eth0 && sudo ifup eth0

You should immediately experience an improvement in your Internet speed.

After I updated Dapper, pages loaded very slowly until I made these changes. 
I researched the solution on [https://forum.bytemark.co.uk/viewtopic.php?pid=1790](https://forum.bytemark.co.uk/viewtopic.php?pid=1790) as well as other Ubuntu forum entries.

---

### Post by l951b951 on 2007-08-13
Data Doctor, you're great.  This worked for me flawlessly.  One problem, my router, Linksys WRT300N, only had 1 DNS server, but listed it twice.  But still, this worked.


> **Data Doctor said:**
> I found a solution:

 Ubuntu is having difficulty with DNS because of miscommunication with your router (related to wrong ports).

  Establishing a direct DNS connection solves the problem. No need to disable IPv6!

1. Find your DNS servers. You may need to check your router settings (usually 192,168.1.1 or 192.168.0.1). Look for a status tab, or similar with the current DNS information. Write down your DNS servers (x.x.x.x & x.x.x.x).

You may wish to back up your dhclient.conf file at this point. In the Terminal, type:
cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.bak

2. Enter these DNS servers directly in your dhclient.conf file:

sudo gedit /etc/dhcp3/dhclient.conf

You should see your dhclient.conf file displayed (with text in it). Add two lines to the end:

supersede domain-name-servers x.x.x.x,x.x.x.x;
    prepend domain-name-servers x.x.x.x,x.x.x.x;

The x's represent your DNS server IP addresses that you found in Step 1.

Save your dhclient.conf file, close gedit and return to the Terminal.

Now restart your DNS lookup with (assuming eth0 is your connection to the router):

sudo ifdown eth0 && sudo ifup eth0

You should immediately experience an improvement in your Internet speed.

After I updated Dapper, pages loaded very slowly until I made these changes. 
I researched the solution on [https://forum.bytemark.co.uk/viewtopic.php?pid=1790](https://forum.bytemark.co.uk/viewtopic.php?pid=1790) as well as other Ubuntu forum entries.

---

