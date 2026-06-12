---
title: "How do I remove a pppoe connection"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Taurus52 on 2008-01-02
When I first set up gutsy on this machine my router died so I had to setup a PPPOE connection which I did w/ pppoeconf.  Now I've replaced the router and it handles the pppoe connection chores. (modem is set to bridge mode).  The PPPOE connection starts at startup every time.  I have to uncheck "Enable Networking" and then check it again to get out to the internet, but something in the configuration of the network is messing up my Samba connection.  Yhe gutsy machine does not appear in the windows network and cannot be seen from other machines, but the shared folder with virtual box works in 1 direction only, from virtual box to linux.  i have XP running in virtualbox.  How can I fix this short of a wipe and reinstall?  I've searched and seen a lot on installing pppoe but nothing on removing it and removing the attempt to start the connection at startup.  I uninstalled all the pppoe pkgs thru synaptic hoping to fix this but no joy

---

### Post by tech9 on 2008-01-02
what kind of router is it?

---

### Post by Taurus52 on 2008-01-02
The router is a Linksys WRT54G, but the router does not seem to be the issue the networking when restarted pulls an address immediately, it just seems to be looking for the pppoe connection first. When I want it to just go to eth0 on boot

---

### Post by tech9 on 2008-01-02
> **Taurus52 said:**
> The router is a Linksys WRT54G, but the router does not seem to be the issue the networking when restarted pulls an address immediately, it just seems to be looking for the pppoe connection first. When I want it to just go to eth0 on boot

So you do have the linksys programmed to authenticate with pppoe then?

---

### Post by Taurus52 on 2008-01-05
> **tech9 said:**
> So you do have the linksys programmed to authenticate with pppoe then?
The new router now does the auth. chores, however before we got the router, while I was setting the system up the old router died. Rather than take the modem out of bridge mode, I just created a PPPoE connection using pppoeconf.  Now with the router in place the system starts up looking to do the pppoe connection that is already established by the router.  To get the machine to connect regularly to the router in a normal way I have to uncheck enable networking in the network icon on the panel then recheck the same thing to get a normal network connection that then connects to the router and accepts a normal dhcp connection.  I can't find a way to undo the pppoeconf and stop ppd from grabbing the connection on startup.  I looked in modules but it is not listed there.  I would like to find what is calling it and just comment it out so if I need it again I can just remove a ;  I'm not certain I'm explaining this clearly.  I'm an old Winblows hand and DOS user and Mac user.  I have more trouble unlearning the stuff that works there so it is not in my way working w/ Linux.  Thanks for trying to understand me.

---

