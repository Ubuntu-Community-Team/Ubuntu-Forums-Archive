---
title: "VPN server"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ibz on 2007-06-18
Hi all, I am a complete noob at linux but do have a fair bit of exp with Microsft computing. 
I would like to connect 3 seperate LANS to my own in the securest way possible, all networks are on individual ADSL connections with different providers. 
I am hoping to setup a Linux server directly on the internet (ie all ports forewarded from my router) with a firewall, it will have VPN services running and with IPSEC /PSK  maintain constant connectivity with other LANS. allowing my internal XP machines to connect directly with remote XP PC's.

My question to all is what software packages would you recommend for the firewall and VPN.

Thanks

Ibz

---

### Post by timcredible on 2007-06-18
openvpn for the vpn.  as for the firewall, iptables is already installed, so you just need a gui - maybe guarddog or shorewall.  they're all in synaptic.

---

### Post by anaconda on 2007-06-18
ssh and sshfs might also be wort looking into.

---

### Post by ibz on 2007-06-20
Thanks for the reply, sorry about the delay in mine,
OpenSwan looks like the solution for my requirements, it would (if configured correctly!!) let my server create a VPN directly with other routers so- that all nodes on the LAN's will be visible to my network. 
as shown here [http://www.jlsnet.co.uk/index.php?page=cc_freeswan](http://www.jlsnet.co.uk/index.php?page=cc_freeswan)

---

