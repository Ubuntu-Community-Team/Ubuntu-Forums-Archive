---
title: "Cisco VPN client help wanted"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-02-13
My college requires a VPN client to get onto the wireless network, and I haven't figured out how to get one to work in Ubuntu, so I'm stuck having to switch back to XP to use the wireless network at school.  I know about VPNC, but I can't figure out how to get it to connect.  I tried to install the Cisco VPN client to see if it would work, but I can't figure out how to install it.  I searched for other Cisco/VPN threads on this board, but they didn't have anything that helped me.

The IT department page at my school has links to the Mac and Linux versions of the Cisco VPN client, but they only offer support for the XP version. :mad: Even with their help, getting it to work in XP was a pain, so I had a feeling that getting it to work in Ubuntu wouldn't be a cakewalk.  Any help would be appreciated!

---

### Post by Oliver W. on 2007-02-14
> **SuperCool4678 said:**
> My college requires a VPN client to get onto the wireless network, and I haven't figured out how to get one to work in Ubuntu, so I'm stuck having to switch back to XP to use the wireless network at school.  I know about VPNC, but I can't figure out how to get it to connect.  I tried to install the Cisco VPN client to see if it would work, but I can't figure out how to install it.  I searched for other Cisco/VPN threads on this board, but they didn't have anything that helped me.

The IT department page at my school has links to the Mac and Linux versions of the Cisco VPN client, but they only offer support for the XP version. :mad: Even with their help, getting it to work in XP was a pain, so I had a feeling that getting it to work in Ubuntu wouldn't be a cakewalk.  Any help would be appreciated!
I assume you're following something along these lines:
1) install vpnc
2) configuration /etc/vpnc.conf :
	[INDENT]Interface name vpnlink
	IPSec gateway ADDRESS
	IPSec ID ipsecclient
	IPSec secret cisco123
	Xauth username LOGIN[/INDENT]
3) start vpn: ```
sudo vpnc-connect
``` or just ```
sudo vpnc
```
4) quit vpn: ```
sudo vpnc-disconnect
```

Make sure that ADDRESS is the location provided by your college (IP-number). LOGIN has to be the login you use for your college. Some colleges use the system where your login is the first initial of your first name and then a couple of letters (6-8 ) of your last name, e.g. "jdenver" if your name is John Denver.

That worked for me (though the installation happened a long time ago). Unfortunately I'm having a problem where my connection stops all of a sudden (random event). If that happens to you too, I suggest installing Cisco's vpnclient, but I'm fiddling with that one right now so can't give you any help on that.

Oh, just noticed this: SuperMike made a [graphical interface for vpnc](http://ubuntuforums.org/showthread.php?t=347308&highlight=Cisco). You can read about it some more, it looks very good.

---

