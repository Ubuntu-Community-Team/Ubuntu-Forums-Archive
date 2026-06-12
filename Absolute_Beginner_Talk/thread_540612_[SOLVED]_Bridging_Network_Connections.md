---
title: "[SOLVED] Bridging Network Connections"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Joeb454 on 2007-09-01
I'm considering moving from WinXP to Feisty, BUT, I have 2 NIC's in the PC (onboard and PCI).

The first is connected to the router, and the second to an Xbox360, and I have the 2 NIC's bridged to allow the 360 to connect to Xbox Live.

Before I switch, I need to know if there is a way to do this in Ubuntu

Any help would be appreciated,

Joe

---

### Post by mikaelsnavy on 2007-09-01
Check out [http://ubuntuforums.org/showthread.php?t=443377&highlight=bridge+network]("http://ubuntuforums.org/showthread.php?t=443377&highlight=bridge+network").

---

### Post by Joeb454 on 2007-09-02
Thanks but thats taking me even more places :P

There needs to be a How-To on this subject, looks like I'm not the only one who wants to know

---

### Post by steve.horsley on 2007-09-02
This article looks good. But instead of compiling the bridging module and att that stuff, just install package bridge-utils.
[http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)
and the VirtualBox manual contains a good description, but again it's written for someone who wants to make a tun/tap adapter to bridge, which you don't in your case. You just want to bridge 2 existing interfaces. I'll keep looking for other howtos, but these should start you off.

I think these commands are probsbly all you need:
[B]sudo aptitude install bridge-utils
sudo brctl addbr br0
brctl addif br0 eth0 promisc
brctl addif br0 eth1 promisc
sudo dhclient br0[/B]

Edit:
This howto looks good - section 6.2 items 1-5.
[http://tldp.org/HOWTO/BRIDGE-STP-HOWTO/set-up-the-bridge.html](http://tldp.org/HOWTO/BRIDGE-STP-HOWTO/set-up-the-bridge.html)

You may have to fiddle with your network settings and stuff to make these changes permanent. I don't have 2 nics so I can't try it out. But in answer to your base question, yes, it's certainly possible. Linux is far more flexible at networking than Windows is. It just doesn't have billions to spend on marketing and corruption.

---

### Post by Joeb454 on 2007-09-02
Oh right thanks, I think I might just have to take the plunge and try to install properly (my PC doesn't want to install it, seem's to be graphics related, lol).

Until I can figure out the installation issues I'm stuck with a VM :(

---

