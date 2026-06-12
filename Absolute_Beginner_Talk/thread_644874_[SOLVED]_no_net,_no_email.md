---
title: "[SOLVED] no net, no email"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-12-19
Having strange probmes with my net access.

I start up firefox and no pages will open... just get that server not found error msg

i open evolution hit send/receive and get:

```
Error while Fetching Mail.

Host lookup failed: pop.tvnet.hu: Name or service not known
```

so I thought I would turn back to epiphany and use it for now.

no luck:

```
File “/usr/share/ubuntu-artwork/home/locales/index-C.html” not found.

Check the location of the file and try again.
```

so what you all think is going on?

Anoghter funny thing is I looked in system and thougth there should be a help menu and/or an about ubuntu menu, but there is not... I seem to rembmer there being one...

I am able to log on to my work account using remotedesktop nad i can run ktorrent and download stuff so there is a net connection. but I have no idea what is wrong with FF, epiphany and evolution...

Robi

Ps I use a router for what it's worth.

---

### Post by NateMan on 2007-12-19
Is this a fresh install? has it worked before? what hardware are you using? ethernet or wifi? have you restarted your network manager or anything? little more info would be very helpful.

---

### Post by beanco on 2007-12-19
sorry,

not a fresh install...

it was working fine until a last night... well epiphany has been down for a while, I just forgot about it.

yesteday I started having the  FF issues... I thought it was due to my ISP. there was a dispute over my bill... BUT I just spoke to them and they say there is nothing wrong, there are no limitations on my account. That it must be a router problem.

Ethernet, not wifi bTW and I have not started my network manager, at least I do not think so....

robi

---

### Post by NateMan on 2007-12-19
what kind of router are you using and what kind of internet?

---

### Post by beanco on 2007-12-19
Net = adsl

Router = not sure... how do you figure it out? sorry to be such a n00b

it says

allied telesyn 

broadband access router

---

### Post by seventhc on 2007-12-19
can you ping?
try to ping yahoo.com
then ping 69.147.114.210
if you can ping by ip but not by name then I would think it's a dns issue.
check dns

ps..have you rebooted>>??
I always reboot first before trying anything else.

---

### Post by Hospadar on 2007-12-19
could you open up a terminal window (Applications->Accessories->Terminal) and run "ifconfig" and post the output here?  as for router, are you plugged directly into the adsl modem, or do you have a router to split the connection over your house?  if so, go to the box thats splitting the connection and try and get a model name/number.  also is this a wired (ethernet) or wireless (wifi) connection.

Also try rebooting your modem and router (if you have one) just unplug them for a few seconds and plug them back in, then restart your machine.

---

### Post by NateMan on 2007-12-19
can you get into your router's settings? also the idea about a reboot is a good one. Always try that first. look up the model numbers on the router and give those out. I have had a similar problem with my isp and sometimes I have to do a dhcp renew.

---

### Post by beanco on 2007-12-19
The first thing I did afte the problems was reboot.

The router splits the connection between to machines... this table top and my wife's laptop, which is not here... if it were I would have tried that too to see what happens.

the router info:

allied telesyn

broadband access router

AT-AR221E

and like I said earlier it is wired not wifi!


Pinging got this

```
rob@rob-desktop:~$ ping 69.147.114.210
PING 69.147.114.210 (69.147.114.210) 56(84) bytes of data.
64 bytes from 69.147.114.210: icmp_seq=1 ttl=55 time=135 ms
64 bytes from 69.147.114.210: icmp_seq=2 ttl=55 time=136 ms

```

ping yahoo.com got

```
ping: unknown host yahoo.com
```

and last but not least

```
rob@rob-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:EB:C7:61  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:feeb:c761/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:32266307 (30.7 MiB)  TX bytes:3243029 (3.0 MiB)
          Base address:0xe800 Memory:fbfe0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

Thanks

Robi

PS  why would the remote desktop work but other stuff not??

---

### Post by seventhc on 2007-12-19
set everything to DHCP
you are pinging ip addresses but not by name, so you are not resolving domain names. I think it's in your router, if you direct connect to your modem, most likely you will connect and resolve domain names.
So you need to configure your router correctly so it resolves domain names.

edit: unplug your modem for about 1 minute, and your router..then: plug in your modem, let it train up...like 1 minute or so until the lights are normal, then plug in your router. Let those lights train, then try your computer.(reboot computer if it doesn't pick it up)

---

### Post by beanco on 2007-12-19
Ok the direct connect should be easy but I have no idea how to configure the router.. I mean what the stuf is in it that is wrong...

robi

---

### Post by seventhc on 2007-12-19
> **beanco said:**
> Ok the direct connect should be easy but I have no idea how to configure the router.. I mean what the stuf is in it that is wrong...

robi
if the direct connect works, then set your router to dhcp.
but first, did you try to power cycle everything?? unplugging  the modem first...let it train, then router, let it train, then computer's? Not sure if I'm saying this right, but I hope that you understand my meaning.

---

### Post by beanco on 2007-12-20
I turned off everything, unplugged the modem and the router

plugged in the modem, let it warm up.. the lights came on..

then the router, waited for the lights.

then the computer and no luck.

I tried the drirect plug in, that did not work.

BUT there are other *boxes* with wires/lines coming in and out. I could have connected the wrong one.

It is dark and cramped where all these wires are so I was not sure which was which.

I will have to tear it all out tonight and see....

As to setting the dhcp... not sure how to do it... mazbe it is time to call the guz who set up the router for me...

robi

---

### Post by seventhc on 2007-12-20
If the direct connect doesn't work either, then it will porbably be a different issue. if you go to the terminal and type in
```
ifconfig
```
what's your output?

---

### Post by beanco on 2007-12-20
> **seventhc said:**
> If the direct connect doesn't work either, then it will porbably be a different issue. if you go to the terminal and type in
```
ifconfig
```
what's your output?

well, yesterday i got this

```
rob@rob-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:EB:C7:61  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:feeb:c761/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:32266307 (30.7 MiB)  TX bytes:3243029 (3.0 MiB)
          Base address:0xe800 Memory:fbfe0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

robi

---

### Post by beanco on 2007-12-20
got home tonigt
fired up the box and hit send/receive in evolution and it downloaded my mail!!!

Opened FF and it opened this site [www.pizzahut.hu](www.pizzahut.hu)

but it iwll not open other sites! That seems very wierd to me.

Robi

edited to add... seems like I can access any .hu site but not any other... no .com, no .net no .org no .de, no .nr , no .de

---

### Post by beanco on 2007-12-21
just tried again and still cannot get foreign web sites to work

anz ideas what is going on?


Robi

---

### Post by seventhc on 2007-12-21
Thats strange, if you can get mail and see pizzahut.hu then I don't understand why you can't see all sites.. What sites are you trying to view? I'd like to see if I can view them.
I'm stumped unless there are policies put in place restricting access.

---

### Post by beanco on 2007-12-21
Well I am stumped too.

I asked the sys op here where I teach and just looked befuddled. then asked if my ISP is having some problem with foreign sites... and went on to say that would make no sense...


i tried the following sites

[www.telemarktips.com](www.telemarktips.com)

[www.ebay.de](www.ebay.de)

[www.unbuntuforums.org](www.unbuntuforums.org)

[www.jasna.sk](www.jasna.sk)

[www.ford.com](www.ford.com)

[www.imdb.com](www.imdb.com)

[www.utazas.com](www.utazas.com)

but they all work if I log in remotely from home to work and go through that computer.

could it be some setting on my computer??? on the browswer????

robi

---

### Post by seventhc on 2007-12-21
If you can get to those sites when logging in remotely then I would say it is a setting somewhere. Do you have a second browser to test with? If it works on a second browser then you will know it is a setting in the main browser, If both browsers don't work then it's probably a setting in your computer...maybe a firewall??

---

### Post by beanco on 2007-12-21
not a fire wall I have never set one up. so I assume I do not have one.


I cannot get epihpany to launch... maybe I can reinstall it and try it.
or tell me some other one to try.

opera was a bomb I could not get it installed at all.

robi

---

### Post by seventhc on 2007-12-21
you can try galeon. it's in add/remove...just make sure the upper right corner is set to 'all open source apps'

---

### Post by beanco on 2007-12-21
what about apt-get install galeon?

I  will try it when I get home

robi

---

### Post by seventhc on 2007-12-21
```
sudo apt-get install galeon
```
should work

---

### Post by beanco on 2007-12-21
should, but doesn't

I go tthis


```
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com feisty/universe galeon-common 2.0.2-4ubuntu1
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com feisty/universe galeon 2.0.2-4ubuntu1
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/g/galeon/galeon-common_2.0.2-4ubuntu1_all.deb  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/g/galeon/galeon_2.0.2-4ubuntu1_i386.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

when I tried to use add/remove I got this


```
CW: Failed to fetch
http://archive.ubuntu.com/ubuntu/pool/universe/g/galeon/galeon-common_2.0.2-4ubuntu1_all.deb
  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch
http://archive.ubuntu.com/ubuntu/pool/universe/g/galeon/galeon_2.0.2-4ubuntu1_i386.deb
  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch
http://archive.ubuntu.com/ubuntu/pool/universe/g/gmail-notify/gmail-notify_1.6.1-3_all.deb
  Could not resolve 'archive.ubuntu.com'

```

Tried to open epiphany and got this

```
File “/usr/share/ubuntu-artwork/home/locales/index-C.html” not found.

Check the location of the file and try again.
```

The only thing I changed before this all started was to open ktorrent.... I do not remember making any changes though.

robi

---

### Post by seventhc on 2007-12-21
I'm at a loss

---

### Post by beanco on 2007-12-22
hi,

I just tried out the wifes laptop with windows whatever versionon it.

works like a charm.

I then switched the cables from the router and the lptop still worked fine, the Ubuntu box did not conect to the net. and now the email does not work at all either. sazs it cannot find the server pop.tvnet.hu

any ideas?


robi

---

### Post by bapoumba on 2007-12-23
Please post the output to :
```
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by beanco on 2007-12-23
Here you go:

[PHP]rob@rob-desktop:~$ rob@rob-desktop:~$ cat /etc/network/interfaces
bash: rob@rob-desktop:~$: command not found
rob@rob-desktop:~$ auto lo
bash: auto: command not found
rob@rob-desktop:~$ iface lo inet loopback
bash: iface: command not found
rob@rob-desktop:~$ 
rob@rob-desktop:~$ auto eth0
bash: auto: command not found
rob@rob-desktop:~$ iface eth0 inet static
bash: iface: command not found
rob@rob-desktop:~$ address 192.168.1.100
bash: address: command not found
rob@rob-desktop:~$ netmask 255.255.255.0
The program 'netmask' is currently not installed.  You can install it by typing:
sudo apt-get install netmask
Make sure you have the 'universe' component enabled
bash: netmask: command not found
rob@rob-desktop:~$ gateway 192.168.1.254
bash: gateway: command not found
rob@rob-desktop:~$ 
rob@rob-desktop:~$ auto eth1
bash: auto: command not found
rob@rob-desktop:~$ iface eth1 inet dhcp
bash: iface: command not found
rob@rob-desktop:~$ 
rob@rob-desktop:~$ auto eth2
bash: auto: command not found
rob@rob-desktop:~$ iface eth2 inet dhcp
bash: iface: command not found
rob@rob-desktop:~$ 
rob@rob-desktop:~$ auto ath0
bash: auto: command not found
rob@rob-desktop:~$ iface ath0 inet dhcp
bash: iface: command not found
rob@rob-desktop:~$ 
rob@rob-desktop:~$ auto wlan0
bash: auto: command not found
rob@rob-desktop:~$ iface wlan0 inet dhcp
bash: iface: command not found
rob@rob-desktop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search barczi.elte.hu


nameserver 157.181.3.1
nameserver 157.181.12.1
nameserver 157.181.42.42
[/PHP]

---

### Post by bapoumba on 2007-12-23
Please run again the **cat /etc/network/interfaces**, the output is really strange. Just paste it in a post.

About **/etc/resolv.conf**, 157.181.3.1 is the IP for Eotvos Lorand University of Sciences in Budapest. Your router IP should appear here.

Did you install ubuntu from a univ connection, and then take the computer home?
What do you get if you run:
```
ping 192.168.1.1
```
(This is the standard IP for private routers).

---

### Post by beanco on 2007-12-23
rob@rob-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




I got the live CD from a collegue at the highschool I teach at.. no idea where he got it...

I also teach at a college and the IT guys there once were trying to help with my net connection and wanted to set up the dchp stuff... think that is the eotvos Lorand stuff....

but the guy who set up the router for me made it static, if that is what you call it.

robi

---

### Post by beanco on 2007-12-23
the ping


rob@rob-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable
From 192.168.1.100 icmp_seq=4 Destination Host Unreachable
From 192.168.1.100 icmp_seq=6 Destination Host Unreachable
From 192.168.1.100 icmp_seq=7 Destination Host Unreachable
From 192.168.1.100 icmp_seq=8 Destination Host Unreachable

---

### Post by bapoumba on 2007-12-23
Hmm, we'll suppose the static stuff is working. Not knowing what is your ISP DNS server IP or you router IP, you can try to use OpenDNS.

Please backup the file:
```
sudo cp /etc/resolv.conf /etc/resolv.conf_bak
```

Edit th file:
```
sudo nano /etc/resolv.conf
```
and change it for:
```
nameserver 208.67.222.222
nameserver 208.67.220.220

```
Or place there your ISP DNS server if you happen to know the IP.

Save the file with ctrl-o (same name, hit enter) and exit nano with ctrl-x.

Should work without restarting the network services or rebooting.

---

### Post by beanco on 2007-12-23
could I just look up either of those DNS?

I guess I could find outt on my system what the DNS is for the router...

and for the ISP, I could look them up... at [www.tvnet.hu](www.tvnet.hu)

robi

---

### Post by bapoumba on 2007-12-23
Sorry, I do not speak Hungarian ^^
I use openDNS from home, you can give it a try.

---

### Post by beanco on 2007-12-23
no, no, no, sorry.. i will look up the dns but i can try this opendns, what ever that is...

robi

---

### Post by bapoumba on 2007-12-23
here you go :)
[http://en.wikipedia.org/wiki/OpenDNS](http://en.wikipedia.org/wiki/OpenDNS)
[http://www.opendns.com](http://www.opendns.com)

---

### Post by beanco on 2007-12-23
Hey ther,e

I am about to follow those links... but guess what.

I am currently using my FF and not the remote log in at work!!!

Thanks

Now to get that epiphany thing taken care of!

robi

---

### Post by beanco on 2007-12-23
oh, yeah, if you have the time/energy, could you explain what you had me do?

what was the dns you had me put in and why did it work?

If you are at all sure, tell me what happened to my computer in the first place?

robi

---

### Post by bapoumba on 2007-12-23
From your other thread (the one with epiphany, where you indicated this one), you had an error "could not resolve hostname". This means, at least, a DNS problem.

I'm not so tech savvy, others may want to describe your problem and the solution with real tech words ^^

Each machine on the internet is identified by an IP, which is a set of numbers not easy to remember by humans. DNS (Domain Name System) is a service that allows to make a correspondence between your words (for ex [www.google.com](www.google.com)) and the IP of the machine your browser should access (72.14.207.99 for google.com). It's the same for every protocol, http etc.
DNS servers are providing you with this feature.

If your network service does not know where to look for IPs, well, you are stuck (you can still use the real IP in your browser and it should work). Usually, ISPs provide a DNS server. I use openDNS because my ISP server is not reliable, it goes off from time to time.

[http://en.wikipedia.org/wiki/Domain_name_system](http://en.wikipedia.org/wiki/Domain_name_system)

---

### Post by beanco on 2007-12-23
ok, thanks!

robi

---

