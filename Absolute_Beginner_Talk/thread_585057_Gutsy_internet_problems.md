---
title: "Gutsy internet problems"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-10-21
well, i managed to convince my friend to try ubuntu

i gave him Gutsy's install disc, he installed Gutsy

now, he has some serious internet problems
he uses Ethernet with Router

 
first of all, in Pidgin, only the ICQ works, not the msn
second of all, here is a list of working and non-working sites which he tried:
working:
[www.google.co.il](www.google.co.il)
[www.izra.co.il](www.izra.co.il)
google search
[http://en-us.www.mozilla.com/en-US/firefox/central/](http://en-us.www.mozilla.com/en-US/firefox/central/)
windows.com - only the main page
download.com - only the main page

non-working:
[www.morfix.co.il](www.morfix.co.il)
[www.net-college.co.il/rabin](www.net-college.co.il/rabin)
[http://www.apple.com/quicktime/download/](http://www.apple.com/quicktime/download/)

---

### Post by snl2587 on 2007-10-21
When you say that certain websites do not work do you mean that nothing is being sent or received or there is a connection problem? It seems a bit strange that some websites would work and others wouldn't.

---

### Post by asakurax on 2007-10-21
> **snl2587 said:**
> When you say that certain websites do not work do you mean that nothing is being sent or received or there is a connection problem? It seems a bit strange that some websites would work and others wouldn't.

mm, i mean he gets a "Server Not Found" ff error

---

### Post by asakurax on 2007-10-21
also, he says Synaptic refuses to download any packages

---

### Post by misfitpierce on 2007-10-21
Those websites marked as not working work for me in firefox just fine.

---

### Post by asakurax on 2007-10-21
> **misfitpierce said:**
> Those websites marked as not working work for me in firefox just fine.

lol
thats the whole problem......
he has some really drastic internet problems with Gutsy

---

### Post by Ubuntnub on 2007-10-21
I am having the same problem since I upgraded Ubuntu.  I can not access the internet any more.  It seems that my network is recognised but I can't load web pages or upgrade software.  Any ideas?
Thanks.

---

### Post by C4nc3l on 2007-10-21
> **Ubuntnub said:**
> I am having the same problem since I upgraded Ubuntu.  I can not access the internet any more.  It seems that my network is recognised but I can't load web pages or upgrade software.  Any ideas?
Thanks.

Same problem, i can telnet to my router so ubuntu found lan but no internet :(

---

### Post by asakurax on 2007-10-22
Help plz (AKA bump)

---

### Post by Pinger05 on 2007-10-22
I know this will be a pain in the neck but have him install 7.04 and see if he still has the problem...  Since you stated that it is a new load there should be little/no data to back up.

With a few people having this issue it may be a bug with your card/WAP.  Sorry there isnt much else to try.

---

### Post by asakurax on 2007-10-22
> **Pinger05 said:**
> I know this will be a pain in the neck but have him install 7.04 and see if he still has the problem...  Since you stated that it is a new load there should be little/no data to back up.

With a few people having this issue it may be a bug with your card/WAP.  Sorry there isnt much else to try.

yeah i just told him to install Feisty

ill let you know how things are going

---

### Post by pulz on 2007-10-22
Im having the same problems also.

Think it has something to due with the wireless card or the wireless setup.
My laptop uses av intel 2200bg wireless card if that helps anything.

Im get the same problems as the other users here with webpages not working and synaptic not able to update packages.

I ran apt-get and noticed it tried to connect to the servers using an strange ip adress, didn't look completely valid.
So i did a nslookup and the hostname resolved to a diffrent ipadress, and now then i was able to update my sources kinda (the main mirror atleast).

Also ssh and all such console programs work just fine, so its kinda strange.

---

### Post by Pconfig on 2007-10-22
You should try to type in firefox: about:config

There search for the setting network.dns.disableIPv6 and set it to true.
If that fixes the problem in firefox, means you can browse any page at full speed now, we can get a workaround to make it systemwide. Firefox doesn't save this setting so it'll be gone after a reboot.

Tell me if it works

---

### Post by asakurax on 2007-10-22
> **Pconfig said:**
> You should try to type in firefox: about:config

There search for the setting network.dns.disableIPv6 and set it to true.
If that fixes the problem in firefox, means you can browse any page at full speed now, we can get a workaround to make it systemwide. Firefox doesn't save this setting so it'll be gone after a reboot.

Tell me if it works

nope.
didn't help

---

### Post by stella2657 on 2007-10-22
> **asakurax said:**
> also, he says Synaptic refuses to download any packages
hi I am having  the same problems after upgrading to gutsy, suggest checking if the source lists are all ticked( system, admin, software source.)

---

### Post by asakurax on 2007-10-22
> **stella2657 said:**
> hi I am having  the same problems after upgrading to gutsy, suggest checking if the source lists are all ticked( system, admin, software source.)

yup, all ticked

---

### Post by Absorbed on 2007-10-22
> **C4nc3l said:**
> Same problem, i can telnet to my router so ubuntu found lan but no internet :(

If you can see your lan but not the internet, it could be a DNS problem. You could try System->Admin->Network, adding your router IP address as a DNS server.

---

### Post by mrumble on 2007-10-22
I'm having the same problem. Had to do the workaround to get Firefox to work... but update won't update (apt-get won't work in terminal). HPDV9005CA... was working under Feisty. AND this is the WIRED connection... not wireless, Any help?

---

### Post by coolclassic on 2007-10-23
Same problem here. No internet!!!!!! I had this problem with fiesty so why is it happening again. I am using wire connection which is not recognised at boot this was recognised in fiesty. I can google but I can't use www. I had fixed this in fiesty but I can't remember how I did it any help.

---

### Post by coolclassic on 2007-10-23
Found my original problem with fiesty the same isssue can be contributed to window_scaling. 
here is the link to the thread:
[http://ubuntuforums.org/showthread.php?t=443209&page=2](http://ubuntuforums.org/showthread.php?t=443209&page=2)

---

### Post by bubbalouie on 2007-10-23
The slow connections can sometimes be caused by IPV6 not working well with a particular router, although from memory this was on by default with feisty too, so I do not understand why all the new reports if this is the cause.

Anyway, maybe the following will help (cut and paste from a previous post):

1) In firefox go to about:config then go to the element for IPV6 (network.dns.disableIPv6) and make sure it is set to true.

2) Disable IPV6 on your system, link below for that:

[http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html)

I hope this helps, however I have given bad advice before, so test with caution, though I have had good results with this :)

---

### Post by asakurax on 2007-10-23
already tried that
didnt help

---

### Post by abh83 on 2007-10-23
> **asakurax said:**
> well, i managed to convince my friend to try ubuntu

i gave him Gutsy's install disc, he installed Gutsy

now, he has some serious internet problems
he uses Ethernet with Router

 
first of all, in Pidgin, only the ICQ works, not the msn
second of all, here is a list of working and non-working sites which he tried:
working:
[www.google.co.il](www.google.co.il)
[www.izra.co.il](www.izra.co.il)
google search
[http://en-us.www.mozilla.com/en-US/firefox/central/](http://en-us.www.mozilla.com/en-US/firefox/central/)
windows.com - only the main page
download.com - only the main page

non-working:
[www.morfix.co.il](www.morfix.co.il)
[www.net-college.co.il/rabin](www.net-college.co.il/rabin)
[http://www.apple.com/quicktime/download/](http://www.apple.com/quicktime/download/)


I had a similar issue when I first came to ubuntu in the dapper days. However, I'm no expert and u'll have to search the forum for HowTos. The solution that worked out for me was to install my own network driver via ndiswrapper. So in other words, i used the windows drivers for my network card in ubuntu.

However, if your friend got nothing to lose i would try to reinstall first. Sometimes things simple mess up during installation.

hope this helps and keep us updated!

---

### Post by abh83 on 2007-10-23
btw after installing 7.10 on my system i have been experiencing slow internet connection. Judging by the many threads on the forum it seems there is a networking bug in 7.10. I guess we'll have to wait and see...

---

### Post by steelklvr on 2007-10-23
I may be able to help with the Synaptic not downloading anything problem as I had the same problem myself.

Here is the link to the thread I made, it has the solution inside.

[http://ubuntuforums.org/showthread.php?t=587225&page=2](http://ubuntuforums.org/showthread.php?t=587225&page=2)

Hope this helps.

---

### Post by FXEF on 2007-10-23
Folks, each post sounds like a DNS issue. I'm not running Gusty but go to System > Administration > Networking should open Network Settings > click DNS tab and make sure you have a good DNS server IP. Either use your ISP DNS server or OpenDNS servers.

OpenDNS servers:
208.67.222.222 
208.67.220.220

 
FXEF

---

### Post by Mischa on 2007-10-24
the problem is related to window packet size that routers don't like:

to fix it do the following as root: (sudo su -)

vi /etc/sysctl.conf

add the following two lines

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

sysctl -p

see [http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/") for an excellent explanation

---

### Post by abh83 on 2007-10-27
Nope... I've tried everything! Nothing seems to help! I think it might actually by my lame router but I'm afraid to upgrade the firmware. I've been through this once before and its not pretty sight!! :(

---

### Post by abh83 on 2007-11-03
I guess my router is not the issue after all. It seems to work fine in windows on my machine. Also, my bro has no issues in ubuntu and xp (xp through vmware) from his machine! I'm at loss here. I've tried everything on this thread.

I didn't seem to have this issues in edgy.

The problem remains:
Internet is slow on my machine with occasional speed bursts. Sometimes I even have to reload a page twice.


Is it normal for the connection status to go idle _while_ surfing? (plz view attachment)

I'm running out of ideas!
:confused:

---

### Post by redbullmonsta on 2007-11-03
What response do you see if you ping the website you are trying to load?

Do you see lots of packet loss or does everything seem fine?

If you have high latency or are seeing dropped packets then there is something wrong at the hardware/driver level.

If you get lots of nice low responses for say 20-30 pings then i would say the problem is within the software layer i.e firefox.... or at least firefox is using a screwed config from somewhere..

good luck

---

### Post by abh83 on 2007-11-03
```
~$  ping -c 20  www.deviantart.com
PING www.deviantart.com (198.172.81.21) 56(84) bytes of data.
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=1 ttl=49 time=202 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=2 ttl=49 time=201 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=3 ttl=49 time=202 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=4 ttl=49 time=202 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=5 ttl=49 time=203 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=6 ttl=49 time=203 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=7 ttl=49 time=201 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=8 ttl=49 time=201 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=9 ttl=49 time=205 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=10 ttl=49 time=201 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=11 ttl=49 time=202 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=12 ttl=49 time=201 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=13 ttl=49 time=202 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=14 ttl=49 time=199 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=15 ttl=49 time=200 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=16 ttl=49 time=204 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=17 ttl=49 time=203 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=18 ttl=49 time=201 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=19 ttl=49 time=201 ms
64 bytes from www.deviantart.com (198.172.81.21): icmp_seq=20 ttl=49 time=201 ms

--- www.deviantart.com ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 28039ms
rtt min/avg/max/mdev = 199.793/202.265/205.385/1.339 ms
```

```
~$ ping -c 20  www.google.com
PING www.l.google.com (209.85.129.147) 56(84) bytes of data.
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=1 ttl=243 time=26.9 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=2 ttl=243 time=25.4 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=3 ttl=243 time=24.6 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=4 ttl=243 time=24.1 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=5 ttl=243 time=26.6 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=6 ttl=243 time=23.4 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=7 ttl=243 time=26.6 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=8 ttl=243 time=24.0 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=9 ttl=243 time=25.8 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=10 ttl=243 time=24.3 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=11 ttl=243 time=26.9 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=12 ttl=243 time=26.2 ms
64 bytes from 209.85.129.147: icmp_seq=13 ttl=243 time=25.8 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=14 ttl=243 time=27.9 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=15 ttl=243 time=22.9 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=16 ttl=243 time=23.9 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=17 ttl=243 time=22.8 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=18 ttl=243 time=26.0 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=19 ttl=243 time=23.0 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=20 ttl=243 time=24.0 ms

--- www.l.google.com ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 41114ms
rtt min/avg/max/mdev = 22.808/25.101/27.990/1.515 ms
```

thx!
i'm no pro but it seems fine to me. I've also installed opera and i still end up with slow surfing speeds. I don't think this issue relates to ff only.

Are there any scans/test that i can carry out? (preferably without having to install additional software)

---

### Post by natehatewindows on 2007-11-03
> **Ubuntnub said:**
> I am having the same problem since I upgraded Ubuntu.  I can not access the internet any more.  It seems that my network is recognised but I can't load web pages or upgrade software.  Any ideas?
Thanks.

about the upgrades....

did you change your software sources? go to SYSTEM>>ADMIN>>SOFTWARE SOURCES

---

### Post by abh83 on 2007-11-03
nope i haven't changed the software sources. Also, i did not upgrade to gutsy. I did a fresh install.

---

### Post by mramsey on 2007-11-03
I am running gutsy on 2 pcs and had problems with firefox on one of them. Mine works fine with firefox. try installing Opera for your web browser(its in add remove programs). then at least you can rule out any browser issues.

Opera works fine for my other pc. I think there is an issue with FF.

---

### Post by philinux on 2007-11-03
Mozilla are rushing out 2.0.0.9 cos of stability problems.

---

### Post by abh83 on 2007-11-03
> **abh83 said:**
> ... I've also installed opera and i still end up with slow surfing speeds. I don't think this issue relates to ff only.

:)

---

### Post by abh83 on 2007-11-04
Interesting... I seem to have solved my issue here. But I don't know how this is possible. All I did was to assign a new (internal) ip address to my computer. :)

---

### Post by eddiegorma on 2007-11-05
Hi with Gutsy the default setting is for ipv6 you need to disable this search the forums till you find instructions.  Also to get synaptic to work you need to install OpenDNS.  It seems like a lot of people are having these same problems.  If you search the forums for these you should find instructions I have done it to two systems already but have forgotten where the link is.  I hope this helps. Eddie

---

### Post by carlos1992 on 2007-11-23
didn't work for me :(
 > vi /etc/sysctl.conf

add the following two lines

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

---

### Post by frank002 on 2007-11-23
Disable IPv6 this way:
 Open a terminal window and type
 gksudo gedit /etc/modprobe.d/aliases
 scroll to line that reads alias net-pf-10 and change it to  alias net-pf-10 off
 save the file. That should speed up your internet

---

