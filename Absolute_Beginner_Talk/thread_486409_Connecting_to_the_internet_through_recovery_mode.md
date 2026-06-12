---
title: "Connecting to the internet through recovery mode"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Anthony236 on 2007-06-28
Hi,
I am trying to get Ubuntu Studio 7.04 running on my laptop but there is a problem with the x server.  I checked the forums and found a way to get that working, but I need an internet connection first and since I don't have a gui to work from I have no idea how to connect to the internet.  I have a WEP connection for my wireless.

Basically I just need to know a step-by-step on how to connect to the internet through a terminal.

OR if there is an edgy Ubuntu Studio available for download (I couldn't find one)

If this is mentioned somewhere else and I missed it could I please get a link to where this solution is posted. Any help is appreciated


Thanks,
Anthony

---

### Post by Anthony236 on 2007-06-29
Never mind, I logged on to an Ubuntu chat room and the people there did a great job helping me out.  Just in case anyone else needs this done and has no clue how to do it, here is a step-by-step. (Some steps might not be needed or there might be a much easier or better way to to this.  This worked for me though)

Step 1: EDIT /etc/network/interfaces

     type  "sudo nano /etc/network/interfaces"  and enter password

     There should be two line that say "auto lo" and beneath it "iface lo inet loopback". Now beneath these lines write:
     
     auto <interface>
     iface <interface> inet dhcp
     wireless-essid <network name>
     wireless-key <network key>

When I say <interface> it is the interface for your wireless connection, something like eth0 (mine was eth1).  <network name> is the name of the network you're connecting to and <network key> is the password for that network.

     Now I'm not sure which of the next two steps are necessary or not, but I used both (in this order) and it worked for me.

Step 2:

     type  "sudo ifup <interface>"

Step 3:

     type  "iwconfig <interface>"

Then my internet was working.

---

### Post by harvest316 on 2008-07-05
Thank you!  My laptop's screen went on the blink, and an xorg reinstall gave me a blank screen.  But this worked like a charm.

---

