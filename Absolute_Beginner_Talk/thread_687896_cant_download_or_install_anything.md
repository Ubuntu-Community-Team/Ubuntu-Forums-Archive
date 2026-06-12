---
title: "cant download or install anything"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by pain1337 on 2008-02-04
i keep getting this error when downloading


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/artsbuilder_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/artsbuilder_3.5.8-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.2-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.2-5_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/akode/libakode2_2.0.2-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/akode/libakode2_2.0.2-2ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/juk_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/juk_3.5.8-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/noatun_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/noatun_3.5.8-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by SOULRiDER on 2008-02-04
Did you mess with any proxy settings?

---

### Post by spiderbatdad on 2008-02-04
looks like on loopback. Do you have eth0 enabled? Are you trying to connect through a proxy server?

---

### Post by pain1337 on 2008-02-04
no im not on th network proxy settings it on direct internet connection and youtube dont work either

---

### Post by jan quark on 2008-02-04
you mean no web pages load ?

what are the results of  the terminal commands
```

lspci
```
```

lshw -C network
```
```

iwconfig
```
```

sudo iwlist scan
```
```

cat /etc/apt/sources.list
```

---

### Post by pain1337 on 2008-02-04
this comes out

home@home-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:05.0 Communication controller: Agere Systems Unknown device 0620
01:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
home@home-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:17:31:a1:00:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.110 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
home@home-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

home@home-desktop:~$ sudo iwlist scan
[sudo] password for home:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

home@home-desktop:~$ homecat /etc/apt/sources.list
bash: homecat: command not found
home@home-desktop:~$

---

### Post by jan quark on 2008-02-04
it seems as if your wireless drivers are not installed

check first if there are any restricted drivers inactive in 

system > administration > restricted drivers manager

---

### Post by pain1337 on 2008-02-04
> **jan quark said:**
> it seems as if your wireless drivers are not installed

check first if there are any restricted drivers inactive in 

system > administration > restricted drivers manager
   

it says "Your hardware does not need any restricted drivers."

---

### Post by spiderbatdad on 2008-02-04
4001 is the default port for anon-proxy  He has internet. I wasn't aware he was trying to install wireless. I thought this was a problem fetching sources.

---

### Post by jan quark on 2008-02-04
than check the network settings 
system > administration > network

is there a wireless network displayed?
perhaps you have only to configure it properly I attach my configuration as a picture

---

### Post by pain1337 on 2008-02-04
yeah i do have internet but when i try to use synaptic package installer or the add/ remove programs or even use vlc to watch the family guy stream it gives me an error and wont let me watch anything

---

### Post by jan quark on 2008-02-04
> 4001 is the default port for anon-proxy He has internet. I wasn't aware he was trying to install wireless. I thought this was a problem fetching sources.

I have till now no idea what the problem is :)

but I try to figured out what I would have done :)

---

### Post by pain1337 on 2008-02-04
> **jan quark said:**
> than check the network settings 
system > administration > network

is there a wireless network displayed?
perhaps you have only to configure it properly I attach my configuration as a picture

no its a wired connection not wireless im on a desktop not laptop

---

### Post by spiderbatdad on 2008-02-04
that from needing codecs and flashplayer...but the other issue with sources is related to you installing anon-proxy.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
tar.gz to get you tube working.

---

### Post by pain1337 on 2008-02-04
> **spiderbatdad said:**
> that from needing codecs and flashplayer...but the other issue with sources is related to you installing anon-proxy.


whats anon-proxy

---

### Post by spiderbatdad on 2008-02-04
TOR?  did you install that?

---

### Post by pain1337 on 2008-02-04
> **spiderbatdad said:**
> TOR?  did you install that?

no i didnt install tor

---

### Post by spiderbatdad on 2008-02-04
what do you have in /etc/protocols

---

### Post by pain1337 on 2008-02-04
> **spiderbatdad said:**
> what do you have in /etc/protocols
this:

# Internet (IP) protocols
#
# Updated from [http://www.iana.org/assignments/protocol-numbers](http://www.iana.org/assignments/protocol-numbers) and other
# sources.
# New protocols will be added on request if they have been officially
# assigned by IANA and are not historical.
# If you need a huge list of used numbers please install the nmap package.

ip	0	IP		# internet protocol, pseudo protocol number
#hopopt	0	HOPOPT		# IPv6 Hop-by-Hop Option [RFC1883]
icmp	1	ICMP		# internet control message protocol
igmp	2	IGMP		# Internet Group Management
ggp	3	GGP		# gateway-gateway protocol
ipencap	4	IP-ENCAP	# IP encapsulated in IP (officially ``IP'')
st	5	ST		# ST datagram mode
tcp	6	TCP		# transmission control protocol
egp	8	EGP		# exterior gateway protocol
igp	9	IGP		# any private interior gateway (Cisco)
pup	12	PUP		# PARC universal packet protocol
udp	17	UDP		# user datagram protocol
hmp	20	HMP		# host monitoring protocol
xns-idp	22	XNS-IDP		# Xerox NS IDP
rdp	27	RDP		# "reliable datagram" protocol
iso-tp4	29	ISO-TP4		# ISO Transport Protocol class 4 [RFC905]
xtp	36	XTP		# Xpress Transfer Protocol
ddp	37	DDP		# Datagram Delivery Protocol
idpr-cmtp 38	IDPR-CMTP	# IDPR Control Message Transport
ipv6	41	IPv6		# Internet Protocol, version 6
ipv6-route 43	IPv6-Route	# Routing Header for IPv6
ipv6-frag 44	IPv6-Frag	# Fragment Header for IPv6
idrp	45	IDRP		# Inter-Domain Routing Protocol
rsvp	46	RSVP		# Reservation Protocol
gre	47	GRE		# General Routing Encapsulation
esp	50	IPSEC-ESP	# Encap Security Payload [RFC2406]
ah	51	IPSEC-AH	# Authentication Header [RFC2402]
skip	57	SKIP		# SKIP
ipv6-icmp 58	IPv6-ICMP	# ICMP for IPv6
ipv6-nonxt 59	IPv6-NoNxt	# No Next Header for IPv6
ipv6-opts 60	IPv6-Opts	# Destination Options for IPv6
rspf	73	RSPF CPHB	# Radio Shortest Path First (officially CPHB)
vmtp	81	VMTP		# Versatile Message Transport
eigrp	88	EIGRP		# Enhanced Interior Routing Protocol (Cisco)
ospf	89	OSPFIGP		# Open Shortest Path First IGP
ax.25	93	AX.25		# AX.25 frames
ipip	94	IPIP		# IP-within-IP Encapsulation Protocol
etherip	97	ETHERIP		# Ethernet-within-IP Encapsulation [RFC3378]
encap	98	ENCAP		# Yet Another IP encapsulation [RFC1241]
#	99			# any private encryption scheme
pim	103	PIM		# Protocol Independent Multicast
ipcomp	108	IPCOMP		# IP Payload Compression Protocol
vrrp	112	VRRP		# Virtual Router Redundancy Protocol
l2tp	115	L2TP		# Layer Two Tunneling Protocol [RFC2661]
isis	124	ISIS		# IS-IS over IPv4
sctp	132	SCTP		# Stream Control Transmission Protocol
fc	133	FC		# Fibre Channel

---

### Post by spiderbatdad on 2008-02-04
also check Preferences>>Network Proxy Preferences and make sure direct connection is selected.

---

### Post by pain1337 on 2008-02-04
> **spiderbatdad said:**
> also check Preferences>>Network Proxy Preferences and make sure direct connection is selected.

it is

---

### Post by spiderbatdad on 2008-02-04
could you please post /etc/apt/sources.list  Jan asked for earlier. I think you forgot a space in the command, so you got no output. Or just navigate to it and post it.

---

### Post by pain1337 on 2008-02-04
> **spiderbatdad said:**
> could you please post /etc/apt/sources.list  Jan asked for earlier. I think you forgot a space in the command, so you got no output. Or just navigate to it and post it.

# Internet (IP) protocols
#
# Updated from [http://www.iana.org/assignments/protocol-numbers](http://www.iana.org/assignments/protocol-numbers) and other
# sources.
# New protocols will be added on request if they have been officially
# assigned by IANA and are not historical.
# If you need a huge list of used numbers please install the nmap package.

ip 0 IP # internet protocol, pseudo protocol number
#hopopt 0 HOPOPT # IPv6 Hop-by-Hop Option [RFC1883]
icmp 1 ICMP # internet control message protocol
igmp 2 IGMP # Internet Group Management
ggp 3 GGP # gateway-gateway protocol
ipencap 4 IP-ENCAP # IP encapsulated in IP (officially ``IP'')
st 5 ST # ST datagram mode
tcp 6 TCP # transmission control protocol
egp 8 EGP # exterior gateway protocol
igp 9 IGP # any private interior gateway (Cisco)
pup 12 PUP # PARC universal packet protocol
udp 17 UDP # user datagram protocol
hmp 20 HMP # host monitoring protocol
xns-idp 22 XNS-IDP # Xerox NS IDP
rdp 27 RDP # "reliable datagram" protocol
iso-tp4 29 ISO-TP4 # ISO Transport Protocol class 4 [RFC905]
xtp 36 XTP # Xpress Transfer Protocol
ddp 37 DDP # Datagram Delivery Protocol
idpr-cmtp 38 IDPR-CMTP # IDPR Control Message Transport
ipv6 41 IPv6 # Internet Protocol, version 6
ipv6-route 43 IPv6-Route # Routing Header for IPv6
ipv6-frag 44 IPv6-Frag # Fragment Header for IPv6
idrp 45 IDRP # Inter-Domain Routing Protocol
rsvp 46 RSVP # Reservation Protocol
gre 47 GRE # General Routing Encapsulation
esp 50 IPSEC-ESP # Encap Security Payload [RFC2406]
ah 51 IPSEC-AH # Authentication Header [RFC2402]
skip 57 SKIP # SKIP
ipv6-icmp 58 IPv6-ICMP # ICMP for IPv6
ipv6-nonxt 59 IPv6-NoNxt # No Next Header for IPv6
ipv6-opts 60 IPv6-Opts # Destination Options for IPv6
rspf 73 RSPF CPHB # Radio Shortest Path First (officially CPHB)
vmtp 81 VMTP # Versatile Message Transport
eigrp 88 EIGRP # Enhanced Interior Routing Protocol (Cisco)
ospf 89 OSPFIGP # Open Shortest Path First IGP
ax.25 93 AX.25 # AX.25 frames
ipip 94 IPIP # IP-within-IP Encapsulation Protocol
etherip 97 ETHERIP # Ethernet-within-IP Encapsulation [RFC3378]
encap 98 ENCAP # Yet Another IP encapsulation [RFC1241]
# 99 # any private encryption scheme
pim 103 PIM # Protocol Independent Multicast
ipcomp 108 IPCOMP # IP Payload Compression Protocol
vrrp 112 VRRP # Virtual Router Redundancy Protocol
l2tp 115 L2TP # Layer Two Tunneling Protocol [RFC2661]
isis 124 ISIS # IS-IS over IPv4
sctp 132 SCTP # Stream Control Transmission Protocol
fc 133 FC # Fibre Channel

---

### Post by spiderbatdad on 2008-02-04
nope that's /etc/protocols

---

### Post by pain1337 on 2008-02-04
my bad here it is 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy exaile
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy exaile

---

### Post by spiderbatdad on 2008-02-04
try this ```
sudo apt-get purge anon-proxy
```

---

### Post by pain1337 on 2008-02-04
i run it on terminal and this happened

home@home-desktop:~$ sudo apt-get purge anon-proxy
[sudo] password for home:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxerces27
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  anon-proxy*
0 upgraded, 0 newly installed, 1 to remove and 183 not upgraded.
Need to get 0B of archives.
After unpacking 352kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 106372 files and directories currently installed.)
Removing anon-proxy ...
Stopping Anonymising Proxy Service: anon-proxy.
Stopping Anonymising Proxy Service: anon-proxy.
Purging configuration files for anon-proxy ...
home@home-desktop:~$ 


so it shud work now right?

---

### Post by spiderbatdad on 2008-02-04
2 more commands to run```
HTTP_PROXY=
http_proxy=
```
please mark post as solved if all is well.

---

### Post by pain1337 on 2008-02-04
i still get this error W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.2-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.2-5_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/akode/libakode2_2.0.2-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/akode/libakode2_2.0.2-2ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/juk_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/juk_3.5.8-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by pain1337 on 2008-02-04
i had to install it manualy because it wont let me use the other way

---

### Post by spiderbatdad on 2008-02-04
make sure you run```
sudo apt-get autoremove
HTTP_PROXY=
http_proxy=
``` reboot your system

---

### Post by pain1337 on 2008-02-04
home@home-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxerces27
The following packages will be REMOVED:
  libxerces27
0 upgraded, 0 newly installed, 1 to remove and 183 not upgraded.
Need to get 0B of archives.
After unpacking 4592kB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.
home@home-desktop:~$ 




comes out

---

### Post by spiderbatdad on 2008-02-04
kind of strange I had asked you about anon-proxy an hour ago, and you said you hadn't installed it...yet there it was. I don't kow if something in yor sources list is forcing it...like those Tux family repos at the bottom. I would try # (commenting them out) Dont forget to reboot.

---

