---
title: "Undo net config for VirtualBox: Remove tap1 and br0 PERMANENTLY"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by jcronkhite on 2007-10-03
A while ago, I setup VirtualBox to use the networking configuration as instructed by [this link]("http://www.virtualbox.org/wiki/Advanced_Networking_Linux").  After VirtualBox began crashing consistently while running a guest OS, I switched to VMWare Workstation 6.  After 4 months now I can say it appears to be bullet proof compared to VirtualBox (I don't want to start a ware between VirtualBox and VMWare, this is just my experience).

Now I'm left with the bridge br0 and a tunnel tap1 that I would like to permanently remove.  As of right now, I have to remove them manually after each reboot.

After manually taking down the bridge br0 and the tap1, then removing them using "brctl delbr br0" and "tunctl -d tap1" respectively, I commented out the lines that are no longer needed by "/etc/network/interfaces".  Here is the output of that file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


```

The problem is, when I reboot, all of the settings are reverted back to use br0 and tap1.  I'm sure I'm unaware of another file to prevent these from being used.

Any suggestions?  Thanks as usual, I love this community!

---

### Post by jordanmthomas on 2007-10-03
I'm not too experienced with VMs, but is it possible that VirtualBox made an init script (in /etc/init.d) that might set its interfaces up?  I'd figure it's worth a check.  (I'd check myself but I don't use Ubuntu or VMs, so it wouldn't be of much help)

---

### Post by jcronkhite on 2007-10-03
No dice, but I did find an old file left over from the install.  So for now, I still do the following after booting up:

```

sudo tunctl -d tap1

sudo ifconfig br0 down

sudo brctl delbr br0

```

Still need to prevent them from being created.  I'll keep digging of course, but hopefully someone can point where my stupidity lies.

Thanks for the info!

---

### Post by jcronkhite on 2007-10-04
Anyone else?  Still no luck for me.  I'll resort to a fresh install of 7.10 in 15 days if I need to I guess, but would prefer an upgrade.

---

### Post by jcronkhite on 2007-10-07
bump?

---

### Post by bodhi.zazen on 2007-10-07
Well, where did you configure the bridge ?

Try looking at /etc/rc.local to see if the bridge is configured there, in which case we can commnet out the appropriate lines.

---

### Post by jcronkhite on 2007-10-19
Thanks for getting back on this.  I actually just did a fresh install of 7.10 so the issue is not present on this config.  But thanks for the info, I'll be sure to check that file if ever I find myself in a similar situation.  Thanks!  

CASE CLOSED

---

### Post by CoronaBVW on 2007-11-20
To Remove the Interface use this tool:

VirtualBox host networking interface creation utility, version 1.5.2
(C) 2005-2007 innotek GmbH
All rights reserved.

Usage: **VBoxDeleteIF <interface name>**
Delete the permanent interface <interface name> from the host system.

---

