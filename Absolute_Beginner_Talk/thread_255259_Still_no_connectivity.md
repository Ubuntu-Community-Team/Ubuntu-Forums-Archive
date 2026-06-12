---
title: "Still no connectivity"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Roph on 2006-09-11
I'm suspecting because of the IPv6 usage.

I've of course got firefox working over IPv4, thanks to the **about:config** ~ network.dns.disableIPv6 thing, though ubuntu itself I beleive is still trying to use IPv6, and so I can't get to things like easyubuntu or use GAIM.

I've read that to stop ubuntu using IPv6 all I have to do is create 

**/etc/modprobe.d/bad_list** and insert this line: 

**alias net-pf-10 off**

Which I've done, and rebooted as suggested, though still no luck.

I'm connected via standard ethernet (eth0) to an Edimax AR6024WGA. (maybe worth nothing that if you google for AR6024WGA on the first page is a result saying "So, my advice is don't buy an Edimax AR6024WGA if you want to access the net on any forms of Linux!") -_-

Any help is of course appreciated ^_~

/etc/modprobe.d/aliases file: (I think you might want this, I'm not sure)

[SIZE="1"]# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
#alias net-pf-10 ipv6
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore[/SIZE]

In /etc/modprobe.d/blacklist I've appended this: 

# blah blah
blacklist ipv6

---

### Post by kidders on 2006-09-11
Turning off IPv6 will not affect your ability to connect to a network using IPv4. All modern operating systems are IPv6 compatible (since it is intended that it will eventually take over altogether), but that shouldn't have anything to do with anything, really.

Your problem is most likely something else. If you can browse the web, you have network access, so that's not what's wrong. Perhaps your network is running a firewall or proxy that's screwing things up for you?

---

### Post by Roph on 2006-09-12
> Your problem is most likely something else. If you can browse the web, you have network access, so that's not what's wrong. Perhaps your network is running a firewall or proxy that's screwing things up for you?

I can browse the net **only** through firefox and **only** after forcing it to not use IPv6.

On a fresh install I have no useful connectivity; I'm assigned an IP but I can't access the outside world. I can with firefox after doing the **about:config** setup and setting **network.dns.disableIPv6** to **true**.

Of course ubuntu itself still tries to use IPv6 and so I'm not able to connect to anything with gaim or browse/download/update any packages or repositories. I'm fairly convinced it's the IPv6 thing; a while back I was using Breezy Badger and my connectivity was perfect.

---

### Post by kidders on 2006-09-12
Hi again,

I've a few questions:

1. Can you access the "inside" world? (ie computers on your own network)
2. I wonder what you mean by "access" ... can you even ping other machines?
3. If not, why not?
4. What address are you assigned?

I'm hoping the answers will help me identify your problem. What makes you suspect the use of IPv6 is causing you trouble anyhow?

---

### Post by Roph on 2006-09-13
> 1. Can you access the "inside" world? (ie computers on your own network)
I can ping / be pinged by other machines. They're all windows though and I'm not actually sure if they have any shares setup, so I don't know as for browsing them. (I beleive I need special software for ubuntu to be able to browse windows network shares though)

> 2. I wonder what you mean by "access" ... can you even ping other machines?
See above ~

> 4. What address are you assigned?
192.168.1.3, as assigned by DHCP.

> What makes you suspect the use of IPv6 is causing you trouble anyhow?

I beleive my trouble isnt actually connecting, I think it is moreso how the OS is trying to use the connection. As I've read, Dapper uses IPv6 by default, whereas Version 5 didn't. I had 5 for a while and everything worked perfectly, and everything connected (i.e. programs such as GAIM and even the OS itself with dealing with packages etc.)

Apart from in firefox where I've forced only IPv4 for dns, I can't connect otherwise; everything fails at the DNS lookup stage.

My router it turns out has possible problems with IPv6, see my first post.

I aprecciate the help you've given so far ;_;

[edit] While googling around on my router model, I came across this:

[http://www.suseforums.net/index.php?showtopic=16708](http://www.suseforums.net/index.php?showtopic=16708)

This guy has the same router as me ;_;

---

### Post by kidders on 2006-09-13
My god, this must be soooo irritating for you!

The first thing I notice is that 192.168.1.3 is an IPv4 address, so at least you have that much. If it were me, the next thing I would check is the contents of **/etc/resolv.conf**. In particular, a line such as **nameserver 192.168.1.1** should be there, giving your Ubuntu box someplace to go for DNS lookups.

I'm also using Ubuntu with an IPv6-incompatible router (it's too old!), but it seems to work fine for me ](*,) 

Next up is to check the output of the **route** command. It's hard to know what it will look like for you, but there should be one line that looks a bit like this:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

```

This indicates the address your computer sends packets that it doesn't know what to do with ... ie stuff destined for the internet.

I hope there's something here that you didn't already know!! Basically, when you're assigned a DHCP address, these are the two most critical pieces of information the DHCP server should be sending with it, without which network connections can be hard to establish. You should make sure that there is at least one nameserver and default route with a familiar-looking (ie IPv4) address ... I'm quietly hoping there isn't :-P

For your own information, you may also be interested in the output of **netstat**, which (among other things) lists all network connections you're making.

With a bit of luck, this'll bring us one step closer to fixing your problem.

---

### Post by coffeecat on 2006-09-13
**Roph**, when I first started with Linux over a year ago, this blasted IPv6 issue plagued me at a time when I knew nothing at all about networking. It was a real b*****, but at least it forced me to learn something about the subject. :wink: Three things worked for me:

1 Disable DNS and set static IP addresses for your machine, gateway (the router) and DNS (your ISP DNS addresses - **not** the router address) in the GUI networking tool. Of course this only works if your router allows you to set static addresses. I believe that not all do. :(

2 Disable IPv6 system-wide. I know you've tried this without success, but have you come across [this thread](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6+firefox)? It starts as a howto for Breezy, but later posters say it doesn't work in Dapper, and some people have posted variations for Dapper. Be warned - it's a long thread.

3 Update the router firmware. This is what fixed it for me once and for all. My understanding is that old or inadequate router firmware is confused by IPv6 modified IPv4 addressing - which is not a problem for the majority of computer users because Windows is not yet enabled for IPv6. Or at least it wasn't when I had this problem. But - from your comment in your first post I suspect that your router is one of those where the manufacturer is either unable or unwilling to do a decent job and update the firmware.

Best of luck.

---

### Post by Roph on 2006-09-22
Just thought I should update; I'm now connected on a new router and everything works perfectly ^_~

Thankyou everybody for the help you have =D.

---

