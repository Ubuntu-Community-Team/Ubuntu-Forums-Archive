---
title: "Online then disconnected"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-22
I have recently installed ubuntu on my desktop (today). I have had it installed for a week on my laptop with no problems. On my desktop, I set up my static ip and yes I did this correctly, and I can get online and browse for awhile and then suddenly I get looking up [www.google.com](www.google.com) or whatever and then the page times out. This is not occuring on any of my other 2 computers using the same network (windows boxes) or my laptop. There is no ip address conflict either. Any idea on what could be causing these problems? All that I have installed is beryl and avant, but the problem was occurring before avant was installed.

---

### Post by irish_flu on 2007-05-22
If it's failing at the "looking up" phase, on first glance it sounds like it could potentially be a DNS problem.  Are the settings for this machine's DNS servers the same as your other boxes?

No guarantees, but it's an easy place to look first.  :)

---

### Post by jba6511 on 2007-05-22
yeah the DNS servers are exactly the same. What gets me is why it works for awhile and then stops working. The other machines are running xp and vista, and the one with ubuntu installed I am triple booting all 3 OS and using xp to post now with no problems.

---

### Post by irish_flu on 2007-05-23
hmmm, that is weird.  It's like your network card goes to sleep after awhile in Ubuntu, or something.  I wonder if some service is timing out after awhile, and it breaks other stuff?

Sorry I'm not more helpful here man, if I think of something I'll holler back.

---

### Post by jba6511 on 2007-05-23
I appreciate it. Seems a few other people have this problem but no def. answers. Do you think reinstalling would work? If so, can I simply format my partition and reinstall?

The problem also effects  syanptic. I was downloading a package for mythtv and about half way through, the download got stuck at 54%.

---

### Post by Wim Sturkenboom on 2007-05-23
When you are experiencing the problem, try [http://64.233.167.99](http://64.233.167.99) in the addressbar of a browser; it should take you straight to google. If that works, it's a DNS problem. If that also does not work, ypur connection died.

I don't know how Synaptic works, but if that also dies, I think that it's not a DNS problem.

---

### Post by jba6511 on 2007-05-23
was able to get online long enough to check this post and then the loading page... and transferring... appeared and no connection. I tried pasting the ip address in and it still could not find the page. Last night while trying to download mythv from synaptic, the computer completely froze. I thought beryl or avant might have something to do with it so I disabled them from running at startup this morning, rebooted, and still the same problem. Any ideas? It is a fresh install so if you guys think reinstalling might help, I can do that as well.

---

### Post by jba6511 on 2007-05-23
anyone? Have searched countless places and can not find any other info on this. Considering installing another distro if I can not get ubuntu to work, but I really like ubuntu. Would kubuntu or debian possibly fix the problem or is this unlikely since ubuntu is built on debian.

---

### Post by jba6511 on 2007-05-23
any ideas? getting desperate and no internet sucks.

---

### Post by pmg on 2007-05-24
I think the first thing is to determine if it's a network conectivity problem, or a DNS (nameserver) problem.  Do you have a local router?  If so, open a terminal window and ping your router.  It's address is probably 192.168.1.1 (but could be 192.168.0.1, or a number of other addresses.) 

> $ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=0 ttl=64 time=1.11 ms
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=16.5 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=12.5 ms


The **ping **command will send a data packet to the router once a second and write out when it gets a reply.  Now, watch that window when "things go bad".  Does it keep writing out lines from reply packets?  Do the reply times go way up?  Does it print out any error messages like "destination unreachable"?  If you don't have a router, you could ping something like yahoo.com, but some ISPs block ping packets so that not working may not really indicate a problem (but it working at first and then stopping after a bit would.)

BTW: to stop the pings press ^C (that hold down the "ctrl" key and press the "C" key)

---

### Post by Wim Sturkenboom on 2007-05-24
To add to above post:
if your firewall is active, it might block ping. The 'standard' Ubuntu firewall rules do that (at least on my Dapper box).

---

### Post by jba6511 on 2007-05-24
Reinstalled ubuntu and everything was working long enough to download system updates, nvidia drivers, and avant. I set the static Ip to 192.168.1.101 -> The same as my other settings in XP and Vista, and everything was working fine for a while. Here are the results when everything was working:

ping 192.168.1.1
64 Bytes from 192.168.1.1: icmp_seq = 1 ttl = 64 time = 1.33 ms
...
64 bytes from 192.168.1.1: icmp_seq = 36 ttl = 64 time = 1.02 ms
36 packets transmitted, 36 recieved, 0% packet loss, time = 35136 ms
rnt min/avg/max/mdev = 1.017/1.051/1.332/0.018 ms

And then when it was no longer working:

From 192.168.1.101: icmp_seq = 1 Destination Host Unreachable
...
12 packets transmitted, 0 recieved, +7 errors, 100% packet loss, time 11009 ms

It worked fine for about 15 minutes and then suddenly stopped. No disconnected from the network errors this time around.

---

### Post by jba6511 on 2007-05-24
night crowd, little help anyone?

---

### Post by jba6511 on 2007-05-24
damn no one can help. I really like ubuntu on my laptop as an OS but it looks like no one can resolve this. Should I report it as a bug?

---

### Post by wormser on 2007-05-24
It sounds a lot like a DNS issue I solved yesterday on a windows box.  The system could load pages after a boot but would stop shortly after.   Just to rule that out change the DNS to 4.2.2.2 and 4.2.2.1.

---

### Post by jba6511 on 2007-05-24
ok will do. Also running lspci my ethernet controller comes up listed as Marvell Technology Group Ltd. Unknown Device 4364 (rev 12). I do not know if that matters. I will try changing the DNS and report back.

---

### Post by jba6511 on 2007-05-24
while I have internet, this might add some info

blake@Ubuntu-Desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by jba6511 on 2007-05-24
sorry for the multiple posts but I want to get it all in before i loose connection. I also heard some people have had luck doing pci=noacpi 

I have this line in my /boot/grub/menu.lst

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=443a327b(bunch of other numbers and letters) ro single

also if that helps

---

### Post by jba6511 on 2007-05-24
works with dns at 4.2.2.2 and 4.2.2.1 for now


...2 min later and no internet (posting from windows box)

---

### Post by irish_flu on 2007-05-25
Man, I have no idea what this could be.  This might seem like a dumb question, but there's no other device on your local network that might be trying to grab (or is already using) the IP address this thing is getting, is there?

---

### Post by wormser on 2007-05-25
> **jba6511 said:**
> works with dns at 4.2.2.2 and 4.2.2.1 for now


...2 min later and no internet (posting from windows box)

That rules out a DNS issue.  

I found a [suse forum]("http://suseforums.net/lofiversion/index.php/t25014.html") with simular issue.   It looks like it got resolved from this quote.

> Edit /etc/modules.conf. Just locate the name of the module and turn it off using the following syntax (or add/append line):
alias modulename off

Read the whole thread and if that does not work start reading all the pages from this [search]("http://www.google.com/search?q=Marvell+Technology+Group+Ltd.+Unknown+Device+4364+%28rev+12%29&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

Good luck and make sure to post your resoluton.

---

### Post by jba6511 on 2007-05-25
I found this page discussing a workaround but this is all nonsense to me as far as making the change happen goes. Still a newbie.

[http://osdir.com/ml/linux.suse.opensuse.devel/2006-10/msg00205.html](http://osdir.com/ml/linux.suse.opensuse.devel/2006-10/msg00205.html)

and here is a page discussing the problem with my mobo and linux

[http://club.csse.monash.edu.au/~tmccoy/index2.php?option=content&do_pdf=1&id=207](http://club.csse.monash.edu.au/~tmccoy/index2.php?option=content&do_pdf=1&id=207)

basically says the gigabyte 965p s3 boards are unsupported in linux and do not work as far as the ethernet controller goes. Is there a workaround or another distro of linux that supports this MOBO.

---

### Post by pmg on 2007-05-26
Sounds like you're having device driver problems.  Looking at the URLs that have been posted and your description, it seems either the wrong device driver is getting loaded or there's a bug in it, and it's working well enough to run for a while but then things go bad.  I assume you reboot to get it going again.  You might be able to shut down your network and unload/reload the driver module - but that's only going to work for a whlie, not a real fix.

The links talk about rebuilding the kernel module to fix the problem.  I can understand you're being hesitant to do that.  I tried to find other web pages that would be more helpful, but didn't find much. [Here]("http://ubuntuforums.org/showthread.php?t=334561") is one post that looks like the same problem and fixed it rebuilding the module.  I've also seen some posts saying people have had some success by limiting it to 100mb and turning autoneg off, but others have said that didn't work.)   I've saw some recent posts on kerneltrap.org about this, so it's promising that there will be a fix.  You're best bet to get the machine on the net and stable now might be to track down a cheap, supported ethernet card to use in the short term.

---

### Post by jba6511 on 2007-05-26
Well I took the easy way out and found an old NIC card that is working well. Thanks for the help guys.

---

### Post by FrancoNero on 2007-06-05
have this same problem on my old machine here. network disconnects like every minute. totally annoying and without a reason.... weird. it's on 6.06 LTS (LTS for LowTechSystem, haha)

---

