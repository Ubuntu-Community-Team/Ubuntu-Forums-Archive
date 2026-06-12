---
title: "No internet! Plz help!"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by afzalnaj on 2007-08-12
hello....

im a newbie to linux, my internet is not connecting so plz help me

My internet connection is of Connect.net.pk -> Connect Communications

the setup is as following:

My computer is connected to a server through LAN
a dialer is provided for windows through which i connect to the internet

the properties of the dialer after connecting in windows xp are as follows

Device Name : WAN Miniport
Device Type  : vpn
Server type   : PPP
Transports     : TCP/IP
Authentication: MS CHAP V2
Compression   : MPPC
PPP multilink framing : off
server ip address : 125.209.*.*
client ip address   : 125.209.*.*

now the properties of my lan network are as follows:
my ip address : 10.104.130.95
dhcp server 10.104.128.3

and the dns are

10.101.10.1
10.101.10.2

plz tell me how can i set ubuntu up to log in to the internet...i have followed all the guides that i have found but to no avail...please tell me the process from after the installation of ubuntu and in detail.

my ubuntu version in 6.06 LTS (dapper drake)

when i type ipconfig in command prompt in xp i get the following

[FONT="System"]Windows IP Configuration

Ethernet adapter Local Area Connection:
[indent]Connection-specific DNS Suffix  .  : connect.net.pk[/indent]
[indent]IP Address.  .   .   .   .   .   .   .   .  : 10.104.130.95[/indent]
[indent]Subnet Mask.   .   .   .   .   .   .   .  : 255.255.252.0[/indent]
[indent]Default Gateway  .   .   .   .   .   .  :[/indent]

PPP adapter Connect Communications:
[indent]Connection-specific DNS Suffix  .  :[/indent]
[indent]IP Address.   .   .   .   .   .   .   .  .  :125.209.*.*[/indent]
[indent]Subnet Mask .   .   .   .   .   .   .  .  :255.255.255.255[/indent]
[indent]Default Gateway   .   .   .   .   .  .  :125.209.*.*[/indent][/FONT]

thanks

PS: i cannot use aptget because ubuntu is not connecting to the internet..any package or dependencies..i have to download from windows

---

### Post by afzalnaj on 2007-08-12
i've tried a couple of things like pptpconfig... network-manager...network-manager-gnome...but nothing happened

---

### Post by anewguy on 2007-08-12
Are you able to see the Windows network?

---

### Post by afzalnaj on 2007-08-12
yes...im also able to see the sites on lan...the network monitor panel indicates activity...thats the activity of the network which i am able to access

edit:

but it wasnt working when i installed ubuntu...when i changed from dhcp to static it worked...but in xp its not static

---

### Post by undertakingyou on 2007-08-12
so you can see your local network but not the web?  Sounds like a DNS issue.  Replace your DNS entries with 208.67.222.222 and 208.67.220.220 and try that.

---

### Post by afzalnaj on 2007-08-12
in ethernet properties???

---

### Post by anewguy on 2007-08-12
You might be able to glean some ideas out of this post as well:

[http://ubuntuforums.org/showthread.php?t=91370&highlight=connect+ubuntu+to+windows+network]("http://ubuntuforums.org/showthread.php?t=91370&highlight=connect+ubuntu+to+windows+network")

---

### Post by undertakingyou on 2007-08-12
assuming that you are using gnome, you go to System => Administration => Networking and then and the DNS tab add then and make sure that they are the first in the list.

Hope that helps.

---

### Post by afzalnaj on 2007-08-12
> **anewguy said:**
> You might be able to glean some ideas out of this post as well:
[http://ubuntuforums.org/showthread.php?t=91370&highlight=connect+ubuntu+to+windows+network]("http://ubuntuforums.org/showthread.php?t=91370&highlight=connect+ubuntu+to+windows+network")

no man...i only hav one pc...they're talking about sharing a connection with two pcs if im right

> **undertakingyou said:**
> assuming that you are using gnome, you go to System => Administration => Networking and then and the DNS tab add then and make sure that they are the first in the list.

Hope that helps.

ok man im gonna try that now...but y do u think this will work??

---

### Post by afzalnaj on 2007-08-12
oh...i forgot to write the

> 

Device Name : **WAN Miniport *(PPTP)***
Device Type : vpn
Server type : PPP
Transports : TCP/IP
Authentication: MS CHAP V2
Compression : MPPC
PPP multilink framing : off
server ip address : 125.209.*.*
client ip address : 125.209.*.*

---

### Post by afzalnaj on 2007-08-12
> **undertakingyou said:**
> so you can see your local network but not the web?  Sounds like a DNS issue.  Replace your DNS entries with 208.67.222.222 and 208.67.220.220 and try that.

tried it...didnt work...after putting these...not even the lan sites opened and there was no response by

ping [www.google.com](www.google.com)

---

### Post by undertakingyou on 2007-08-12
so now you can't see your lan but you could see it before adding those entries?  Well I thought that it could have been a DNS issue but, I guess not.  Can you post the output of ```
route
```  It may be a routing error also.

---

### Post by afzalnaj on 2007-08-12
here

```
afzal@prostreet:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.104.128.0    *               255.255.252.0   U     0      0        0 eth0
default         10.104.128.3    0.0.0.0         UG    0      0        0 eth0
afzal@prostreet:~$
```

---

### Post by afzalnaj on 2007-08-12
can anyone online right now help me???

---

### Post by afzalnaj on 2007-08-12
can anyone please help????

---

### Post by anewguy on 2007-08-13
> **afzalnaj said:**
> no man...i only hav one pc...they're talking about sharing a connection with two pcs if im right



ok man im gonna try that now...but y do u think this will work??

I think you're missing the point of the post I pointed you to - it should show you how to find/connect to the device (modem) on the network (the server you connect to - consider it just another PC, particularly since you are saying a Windows network).  Read through it carefully, think about what it could be saying to you, not "this isn't what I'm doing so it's not gonna work".  Unfortunately, a lot of the digging for Linux issues involves interpretting what is happening when someone posts something, even if it is not directly your problem.  It's how a lot of us have learned (and I think that is unfortunate, but necessary right now).  You may want to also try the "search" and go to "advanced search" and type in the gist of what you are trying.  Also Yahoo or what ever search engine you like can have posts.  Don't restrict your searches to just Ubuntu - expand them to Linux and you'll find much more.  It's a lot to weed through, but can be worth it.:)

I wish I could provide you with a direct how-to, but I don't have that.  Could you maybe post the results of this back here as well?:)

cat /etc/hosts


Thanks!  Good luck - there's going to be a way, it's just a matter of finding it.  I know some of the posts I have read seem to say you might need to install Samba for this type of access.:)

---

### Post by afzalnaj on 2007-08-13
i can't understand a single word of that thread man...im a complete newbie...i'll try to understand that article...thanks for that link

i installed network-manager and network-manager-gnome...i couldnt install network-manager-pptp or network-manager-vpn

they both kept asking for libraries...but i already had the required libraries on my comp...are they available for dapper coz i downloaded frm here

[http://www.wlug.org.nz/~crb/nm/dapper/](http://www.wlug.org.nz/~crb/nm/dapper/)

but i did install pptpconfig

heres what is says
```
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/0
CHAP authentication succeeded
MPPE required but peer refused
Connection terminated.
pptpconfig: pppd process terminated by signal 10 (failed)
pptpconfig: SIGUSR1
```

and this might not be directly related but this occurs when i stop pptpconfig
both are separate dialog boxes

Unable to remove undo file /var/run/pptpconfig.myvpn.undo

/var/run/pptpconfig.myvpn.undo is not present,
though it was expected to have been written by this program earlier.

im going to post the results of cat /etc/hosts ASAP... 15-20 min

---

### Post by anewguy on 2007-08-13
I have also read other posts on this forum that suggest you need to use Samba (I think that's a server product you can run in Ubuntu, but not sure since I've never used it) to get the type of access you want.:)

---

### Post by anewguy on 2007-08-13
Here's a link to installing/using Samba and it says including making your Ubuntu PC look like a Windows workstation on a LAN.  Sounds like that is what you are doing in Windows XP, so maybe this would be the thing you need.

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")


:)

---

### Post by afzalnaj on 2007-08-13
ok thx will try that...heres the result of cat /etc/hosts

```
afzal@prostreet:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts
127.0.0.1 localhost prostreet
ff00::0 ip6-mcastprefix
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
::1 ip6-localhost ip6-loopback
127.0.1.1 prostreet
ff02::3 ip6-allhosts
afzal@prostreet:~$ 
```

---

### Post by afzalnaj on 2007-08-13
Samba is a free software re-implementation of SMB/CIFS networking protocol...

[http://en.wikipedia.org/wiki/Samba_(software)](http://en.wikipedia.org/wiki/Samba_(software))

from what i understand its related to file sharing isnt it?

---

### Post by afzalnaj on 2007-08-13
Samba is a free software re-implementation of SMB/CIFS networking protocol...

[http://en.wikipedia.org/wiki/Samba_(software)](http://en.wikipedia.org/wiki/Samba_(software))

from what i understand its related to file sharing isnt it..and from the thread i understand that its not related to vpn or pptp?

sry for double posting

---

### Post by vpjr on 2007-08-13
have you tried:

System -> Administration -> Networking

or

(at terminal)

sudo network-admin

??

if you did, what was the resul?

---

### Post by afzalnaj on 2007-08-13
that opens the networking tools gui i think...thats the one where u can traceroute...lookup..whois n stuff..it opens fine

---

### Post by afzalnaj on 2007-08-13
i found this 
[http://reksio.ftj.agh.edu.pl/~tezar/ubuntu/howto.html](http://reksio.ftj.agh.edu.pl/~tezar/ubuntu/howto.html)
plz tell me if this is gonna help

pptpconfig now authenticates with MS CHAP V2 but results this in debug:

```
[FONT="Fixedsys"]pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.12 2006/08/21 06:19:12
# pptp --version
pptp: unrecognized option `--version'
pptp version 1.7.0
Usage:
  pptp <hostname> [<pptp options>] [[--] <pppd options>]

Or using pppd's pty option: 
  pppd pty "pptp <hostname> --nolaunchpppd <pptp options>"

Available pptp options:
  --phone <number>	Pass <number> to remote host as phone number
  --nolaunchpppd	Do not launch pppd, for use as a pppd pty
  --quirks <quirk>	Work around a buggy PPTP implementation
			Currently recognised values are BEZEQ_ISRAEL only
  --debug		Run in foreground (for debugging with gdb)
  --sync		Enable Synchronous HDLC (pppd must use it too)
  --timeout <secs>	Time to wait for reordered packets (0.01 to 10 secs)
  --nobuffer		Disable packet buffering and reordering completely
  --idle-wait		Time to wait before sending echo request
  --max-echo-wait		Time to wait before giving up on lack of reply
  --logstring <name>	Use <name> instead of 'anon' in syslog messages
  --localbind <addr>	Bind to specified IP address instead of wildcard
  --loglevel <level>	Sets the debugging level (0=low, 1=default, 2=high)
# pppd --version
pppd version 2.4.4b1
# uname -a
Linux prostreet 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.15-23-386/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.15-23-386 preempt 486 gcc-4.0
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
# grep mppe /proc/modules
ppp_mppe 7172 0 - Live 0xd0c81000
ppp_generic 30100 2 ppp_mppe,ppp_async, Live 0xd0cab000
Array
(
    [name] => myvpn
    [server] => *********
    [domain] => 
    [username] => ******
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_client_to_lan
    [usepeerdns] => 1
    [require-mppe] => 1
    [nomppe-40] => 
    [nomppe-128] => 
    [refuse-eap] => 1
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => a:0:{}
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.*.*.*    0.0.0.0         255.255.252.0   U     0      0        0 eth0
0.0.0.0         10.*.*.*    0.0.0.0         UG    0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug		# (from /etc/ppp/peers/myvpn)
updetach		# (from command line)
logfd 1		# (from command line)
linkname myvpn		# (from /etc/ppp/peers/myvpn)
dump		# (from /etc/ppp/peers/myvpn)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name cablinks127		# (from /etc/ppp/peers/myvpn)
remotename myvpn		# (from /etc/ppp/peers/myvpn)
		# (from /etc/ppp/options.pptp)
pty pptp ********** --nolaunchpppd 		# (from /etc/ppp/peers/myvpn)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam myvpn		# (from /etc/ppp/peers/myvpn)
proxyarp		# (from /etc/ppp/options)
usepeerdns		# (from /etc/ppp/peers/myvpn)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
require-mppe		# (from /etc/ppp/peers/myvpn)
require-mppe-128		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 3
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x97974a3c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x97974a3c> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0x3ac51c35> <pcomp> <accomp> <callback CBCP>]
sent [LCP ConfRej id=0x0 <callback CBCP>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x97974a3c> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <auth eap> <magic 0x3ac51c35> <pcomp> <accomp>]
sent [LCP ConfNak id=0x1 <auth chap MS-v2>]
rcvd [LCP ConfReq id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x3ac51c35> <pcomp> <accomp>]
sent [LCP ConfAck id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x3ac51c35> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x97974a3c]
rcvd [CHAP Challenge id=0x0 <866f2907df8296184b4ebdc3b4334ac3>, name = "CRRAS2"]
sent [CHAP Response id=0x0 <3779f7f52a415d0cb4ef618c0162bf7a0000000000000000955620c4bede79adf6a6a5c76093c9994aa53c44ed9abe8c00>, name = "******"]
rcvd [LCP EchoRep id=0x0 magic=0x3ac51c35]
rcvd [CHAP Success id=0x0 "S=9B9CA643E3F9CCB972670170729501443CC826FF"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [CCP ConfReq id=0x4 <mppe +H -M -S -L -D +C>]
sent [CCP ConfNak id=0x4 <mppe +H -M +S +L -D -C>]
rcvd [IPCP ConfReq id=0x5 <addr 125.209.*.*>]
sent [IPCP TermAck id=0x5]
rcvd [CCP ConfRej id=0x1 <mppe +H -M +S +L -D -C>]
MPPE required but peer refused
sent [LCP TermReq id=0x2 "MPPE required but peer refused"]
rcvd [LCP TermAck id=0x2 "MPPE required but peer refused"]
Connection terminated.
Waiting for 1 child processes...
  script pptp ************ --nolaunchpppd , pid 8891
Script pptp *********** --nolaunchpppd  finished (pid 8891), status = 0x0
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.*.*.*    0.0.0.0         255.255.252.0   U     0      0        0 eth0
0.0.0.0         10.*.*.*    0.0.0.0         UG    0      0        0 eth0
pptpconfig: pppd process terminated by signal 10 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.*.*.*    0.0.0.0         255.255.252.0   U     0      0        0 eth0
0.0.0.0         10.*.*.*    0.0.0.0         UG    0      0        0 eth0[/FONT]

```

---

