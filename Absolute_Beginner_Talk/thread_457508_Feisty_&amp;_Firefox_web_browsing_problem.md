---
title: "Feisty &amp; Firefox web browsing problem"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by deeteesbeard on 2007-05-28
Hi,

I have had a quick search for my problem, but not found anything with the answers yet.
I have just installed ubuntu studio (fiesty) on my pc, on the whole everything seems great but I have a problem with browsing the web.

symptoms are:
Firefox (2.0.0.3) loads [www.google.co.uk](www.google.co.uk) quickly (and performs searches), but waits indefinately for most other websites/domains I have tried ([www.ubuntu.com](www.ubuntu.com) ubuntuforums.org sourceforge.net [www.dtism.co.uk](www.dtism.co.uk)) Some will say 'waiting for .......' occasionnaly I may get as far as 'transferring data from.......' but that's it.

Other programs like apt-get also struggle to get internet access.
[shell output]
dtism@grover:~$ sudo apt-get -s update
Password:
Ign cdrom://Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_GB
20% [Waiting for headers] [Waiting for headers] [Waiting for headers]     
[/shell output]
As you can see, apt-get can't retrieve headers.

I have no trouble accessing the web from windows xp on the same machine (same ethernet port, same adsl router)

I'm going to investigate my router config in case it's a firewall issue, but I wondered if anyone might be able to shed some light on this?

---

### Post by ellisdee on 2007-05-29
Looks like your PC may not be resolving hostnames but it's strange how you can get to Google.

Do you have correct name servers in place in /etc/resolv.conf   ?

Do you get your LAN IP Address via DHCP?

Maybe try from your shell "sudo dhclient" and see whether you obtain an IP from your router again.

Just a few suggestions to get you started anyways ;)

---

### Post by deeteesbeard on 2007-05-29
I turned off my routers firewall and it made no difference.
I can ping by domain name, so it is resolving. Yes, I'm getting my IP address via DHCP. The router itself should be acting as nameserver, I'll have a look at /etc/resolv.conf though.

Thanks for suggestions so far.

Doug

---

### Post by tyk on 2007-05-29
ditto same prob but diff build (dapper on oldish thinkpad).. have static ip

??
thx.

---

### Post by deeteesbeard on 2007-05-29
It's almost as if requests on port 80 aren't beling allowed a response from the webserver. Does ubuntu studio install a firewall of any sort by default?

I haven't tried ftp or email yet (not that I plan to use ubuntu studio to check my emails, but it might help me narrow down the problem).

I noticed in another thread tyk, you were saying you were getting slow download speeds? Does that mean you are managing to open some webpages from the net? Have you had any luck at all finding a solution?

---

### Post by deeteesbeard on 2007-05-30
Latest development.

I tried static settings on my LAN interface. I even used my ISP's nameserver addresses instead of putting my router address. The result was the the same as when using DHCP.

/etc/resolv.conf contained what it should do I think: the dns server address that was set in network manager. So I'm almost 100% sure it isn't a DNS problem.

But it is wider than just port 80: I tried to telnet to my router from a shell and got presented with the login prompt, but after logging in, Telnet only returned half of the router's welcome page, then hung. So it now seems that packets entering my LAN interface are being stopped shortly after they are being received.

Any idea how I narrow this down further? Any analysis tools I can use? Again, does ubuntu install a firewall by default, I haven't seen any sign of one in the program list in gnome, but maybe there's one outside of that?

---

### Post by tyk on 2007-05-30
no luck really. i'm gonna try some inconsistent logic (xp type, just reinstall ;) now and change to xubuntu on the thinkpad. ubuntu installed too many things so it'll def be clogging up RAM. and the machine is quite old, got no more than 128mb ram or something. a same install on my amd 64 with loadsa ram dint create any prob with the net. 
though i don't think that that shd be your prob. your system must be far newer than my thinkpad... 
anyway will keep you updated.

---

### Post by deeteesbeard on 2007-05-30
Yeah my system is probably newer than your thinkpad (Athlon 64 3700+ in an Asus A8N-SLI deluxe mobo with 2GB RAM and a ATI Radion 800 GTO and 4 sata hard disks) the motherboard has built in thernet ports though, one 10/100 and one 10/100/1000 I'm currently using the gigabit one but I'm wondering if the drivers aren't quite right for them? (They were both recognised correctly during set-up although I chose not to set-up networking at that point because the install would hang at the configuring apt-get stage (I think because it was trying to connect to an online repository and failing))

In case you're interested tyk (or anyone else having similar problems) I found this link which offers some troubleshooting advice. [http://www.linuxquestions.org/questions/showthread.php?t=525149]("http://www.linuxquestions.org/questions/showthread.php?t=525149")

I'm going to check it out when I get time.

---

### Post by Haegin on 2007-05-30
Check out all the stuff in the wiki about IPv6 and IPv4.

PS - I am deliberately not giving much information as it is all in the wiki (which is a great resource the use of which should be encouraged)

If you cant find the wiki use Google - that's a good resource too!

---

### Post by deeteesbeard on 2007-05-30
Thanks, I'll do that. Have bookmarked the wiki and will look in there first before posting.

---

### Post by gn2 on 2007-05-30
Could it be an ipV6 issue? 

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

---

### Post by deeteesbeard on 2007-05-30
It possibly could be :)

I'm going to try that out tonight if I get time. I already did the firefox ipv6 disabling which made no difference, but if my hardware can't handle it properly then that might be the problem I'm having.

I'll post my results up when I've tried it out.

---

### Post by bapoumba on 2007-05-30
hello,
could you paste the output to:
```
ifconfig
cat /etc/resolv.conf
cat /etc/hosts
```
What kind of router do you have ?

---

### Post by Ambimom on 2007-05-30
Just a thought....are you running any torrents?  It could be your ISP is limiting your bandwidth.  I had a similar problem and it turned out that in order for pages to load, I had to pause torrents.

---

### Post by pacemaker500 on 2007-05-30
I have had a similar (near identical) problems in using a Compaq Evo 620 to access the web using Firefox1.5 from Ubuntu 6.06. The Laptop was connected into an ethernet port of a WLAN router. A second non Linux machine had no access problems from the same router and port, indicating no problems with firewalls or www connections.

Pluging the "faulty" Laptop into a friends WLAN router (different type) via the ethernet port showed no such problems. I conclude a electrical interfacing problem with DTE or DCE. Will advise if I find the exact cause. I will try next with a long networking cable.

---

### Post by deeteesbeard on 2007-05-30
> **bapoumba said:**
> hello,
could you paste the output to:
```
ifconfig
cat /etc/resolv.conf
cat /etc/hosts
```
What kind of router do you have ?

I'm not at home now so can't show you reslolv.conf or hosts or ifconfig output, but will do that later.

My router/modem is a speedtouch 716wl (as provided by my ISP) It has a 4 port switch and wireless on the lan side, and adsl2+ on the wan side.

I'm also going to investigate the ipv6 thing as detailed in the wiki (kindly pointed out to me earlier in the thread).

Cheers.

> **Ambimom said:**
> Just a thought....are you running any torrents?  It could be your ISP is limiting your bandwidth.  I had a similar problem and it turned out that in order for pages to load, I had to pause torrents.

No, I can barely get a web page to open let alone upload/downoad anything. ;)

---

### Post by bapoumba on 2007-05-30
Moved to "Absolute Beginner Talk" per OP's request.

---

### Post by deeteesbeard on 2007-05-30
Ok, here's the results from ifconfig and the contents of resolv.conf and hosts (in attachment)

I tried disabling IPv6 by editing /etc/modprobe.d/aliases and replacing "alias net-pf-10 ipv6" with "alias net-pf-10 off" (as described in the wiki)

It is still not working though. :(

---

### Post by Austin_KW on 2007-05-30
That attached file is still showing an ipv6 address on your eth1. Did you restart networking /reboot after editing the aliases.

---

### Post by deeteesbeard on 2007-05-30
I did reboot, I have a feeling those results were from before the reboot. I'll redo them. Back in a short while after I've rebooted back into linux.

---

### Post by Austin_KW on 2007-05-30
It also looks like symptoms of an mtu problem. 
When it works on windows are you using any ISP client software that might tunneling your connections or reducing you ethernet mtu?

---

### Post by deeteesbeard on 2007-05-30
I rebooted into ubuntu and re ran ifconfig & cat /etc/hosts and resolv.conf I have attached as output.txt

It's very odd that I can browse a couple of websites fine: [www.nat.org.uk](www.nat.org.uk) and [www.google.co.uk](www.google.co.uk) were great, I even downloaded a pdf from [www.nat.org.uk](www.nat.org.uk). But trying to load [www.ubuntu.com](www.ubuntu.com) or ubuntuforums.org just wasn't happening.

> **Austin_KW said:**
> It also looks like symptoms of an mtu problem. 
When it works on windows are you using any ISP client software that might tunneling your connections or reducing you ethernet mtu?

I'm using a fresh install of windows and I'm not using any kind of special tunnelling software afaik, just a plain old dhcp internet connection attached to my adsl router. I've attached output from an ipconfig /all too. I think the MTU on the connection is 1500

---

### Post by Austin_KW on 2007-05-30
Probably not a path mtu problem then,

Is it only firefox,
What about "wget http://ubuntuforums.org/" from the command line.

Also I notice from your attachment that you have an eth0, same manufacturer, but if it is a different chipset maybe it uses a different driver that might yield better results.

---

### Post by deeteesbeard on 2007-05-31
Not tried wget but w3m behaves the same way as firefox, and a telnet to my router showed similar symptoms.

Eth0 I'll try, but I don't hold much hope to be honest. (Eth1 is a marvell yukon gigabit adapter integrated to the motherboard, Eth0 is also an integrated adapter but based on the nvidia nforce4 chipset)

I'm going away for a week so I'll have to continue this in a weeks time. Thanks for your ideas.

I think I'm going to also try using another router, or upgrading my routers firmware.

---

### Post by bapoumba on 2007-05-31
One thing you could do is ping a site that you can load fine and then ping UF and see if there is any difference.

---

### Post by deeteesbeard on 2007-05-31
I might get time to do that tonight. If I do I'll post results.

---

### Post by tyk on 2007-06-05
hohoho i did it...
or it probably did it itself :)
network flying on feisty.
after two days i booted up my laptop to find pretty much the same pprob.. network got the blues, pinging my modem gives 0% loss but pinging my ISP's DNS was a slugfest.. anything between 70% and 100% loss.
what i did was pinged the DNS with smaller packets (32B) and it happily ponged :)

i dunno if that solved the problem but now internet is here and yippee. am quickly updating ubuntu at a 40kBps clip (which is what i generally get in any case for those who think its still damn slow, i am in india you know)
having a linux machine without net is like having half a horse, ,mostly the back side. try this out. my uneducated guess is that routing on my machine through this particular modem required a smaller packet configuration, which it learnt to do.

cheers to ubuntu and linux (or as i read somewhere, loonix?? ha iscoffatyou, nonbelievers)

---

### Post by tyk on 2007-06-07
another thingy i noticed that avahi has somehow reconfigured itself after i did that. maybe one can try installing a different network manager like this one...
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

cheers.)

---

### Post by deeteesbeard on 2007-06-10
Okay, so here's the results of pinging 3 different url's

ubuntuforums.org - times out in browser

[www.nat.org.uk](www.nat.org.uk) - loads perfectly in browser

[www.google.co.uk](www.google.co.uk) - loads almost perfectly in bowser

```
dtism@grover:~$ ping ubuntuforums.org
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=1 ttl=53 time=13.9 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=2 ttl=53 time=14.4 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=3 ttl=53 time=14.5 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=4 ttl=53 time=13.6 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=5 ttl=53 time=13.3 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=6 ttl=53 time=15.6 ms

--- ubuntuforums.org ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 9995ms
rtt min/avg/max/mdev = 13.350/14.598/18.820/1.482 ms

dtism@grover:~$ ping www.nat.org.uk
PING www.nat.org.uk (81.201.137.36) 56(84) bytes of data.
64 bytes from srv-81-201-137-36.ukfast.net (81.201.137.36): icmp_seq=1 ttl=249 time=21.1 ms
64 bytes from srv-81-201-137-36.ukfast.net (81.201.137.36): icmp_seq=2 ttl=249 time=20.8 ms
64 bytes from srv-81-201-137-36.ukfast.net (81.201.137.36): icmp_seq=3 ttl=249 time=54.3 ms
64 bytes from srv-81-201-137-36.ukfast.net (81.201.137.36): icmp_seq=4 ttl=249 time=20.9 ms
64 bytes from srv-81-201-137-36.ukfast.net (81.201.137.36): icmp_seq=5 ttl=249 time=20.5 ms
64 bytes from srv-81-201-137-36.ukfast.net (81.201.137.36): icmp_seq=6 ttl=249 time=20.2 ms

--- www.nat.org.uk ping statistics ---
16 packets transmitted, 16 received, 0% packet loss, time 15001ms
rtt min/avg/max/mdev = 20.164/23.219/54.366/8.120 ms

dtism@grover:~$ ping www.google.co.uk
PING www.l.google.com (216.239.59.99) 56(84) bytes of data.
64 bytes from gv-in-f99.google.com (216.239.59.99): icmp_seq=1 ttl=248 time=25.1 ms
64 bytes from gv-in-f99.google.com (216.239.59.99): icmp_seq=2 ttl=248 time=24.8 ms
64 bytes from gv-in-f99.google.com (216.239.59.99): icmp_seq=3 ttl=248 time=25.1 ms
64 bytes from gv-in-f99.google.com (216.239.59.99): icmp_seq=4 ttl=248 time=25.1 ms
64 bytes from gv-in-f99.google.com (216.239.59.99): icmp_seq=5 ttl=248 time=24.7 ms
64 bytes from gv-in-f99.google.com (216.239.59.99): icmp_seq=6 ttl=248 time=25.2 ms

--- www.l.google.com ping statistics ---
17 packets transmitted, 17 received, 0% packet loss, time 16006ms
rtt min/avg/max/mdev = 24.676/25.028/25.354/0.251 ms
```

I notice that pinging ubuntuforums is getting a reply much quicker than the other two.

---

### Post by tyk on 2007-06-12
your prob seems to be stranger than mine in any case. all sites are pinging but some are not loading in the browser?? hmm anyway try pinging with different sizes of data and/or a different network manager.
cheersa n bestoluck

---

### Post by tyk on 2007-06-14
i really dunno what is happening. browsers are working fine. every site i am trying gets loaded in normal time. but update manager and add/remove and synaptic are barely connecting at a few Bps like between 0 and 1kBps. its dmn frustrating. somebody please help...

---

