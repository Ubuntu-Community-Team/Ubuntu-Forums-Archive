---
title: "[SOLVED] Internet Cuts out"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Pharisee on 2007-08-27
I ran the live CD and the internet was working fine, after I installed it I noticed the internet would work for a very short period of time (like a minute of so) and then it would stop working. Sometimes the network cable light would go out, so I figured it was a network issue. I have now screwed up some network settings, which I figured I shouldn't of touched to begin with, but I guess I shall just re install.

Can anyone think of what the issue could be? I am with Optus on a ADSL 2 plan, using a [Netgear DG834]("http://www.netgear.com/Products/RoutersandGateways/WiredRouters/DG834.aspx") if any of that information helps. Though my modem has wireless I have that switched off, and have it directly connected.

Also I just remembered I can't seem to log into my modem/router via the usual URL.

Thanks.

---

### Post by carverj on 2007-08-27
Just wondering, have you tested the cable? Just that you mentioned the address to the modem doesn't seem to connect.
Also wondering what changes you made to the network configuration?

---

### Post by Pharisee on 2007-08-27
I have a dual boot, so when I run in in Windows Vista it runs absolutely fine so I don't think it would be a network cable issue.

As for the network settings, I can't remember off the top of my head (not logged into Linux at the moment) but I believe I changed the default IP address as well as another address setting. I changed them to 192.168.0.1 (don't ask me why, I don't know :P ).

Cheers,

---

### Post by Seisen on 2007-08-27
That is most likely the problem, most of the time 192.168.0.1 is the defauilt gateway for routers. Try changing your IP address to 192.168.0.10 or something similar and see if it works.

---

### Post by conjur3r on 2007-08-27
If you are on a DHCP network, I would suggest that you leave your settings in tack until you figure out what is actually happening.  Next time you experience networking issues, open up a terminal and try to ping something such as google using both its name and ip address, eg:

# ping google.com.au
# ping 72.14.203.104

If they don't work, try pinging your router's ip address then report back.

What kind of motherboard do you have?  I only ask because some newish Gigabyte boards set the NIC into sleep mode after windows shuts down and linux cannot enable it.

---

### Post by Pharisee on 2007-08-27
Thanks, I'll give that a shot. Though I did change the setting after I had issues, not before, so I'm not sure it'll do anything *fingers crossed*

---

### Post by Pharisee on 2007-08-27
I have a Gigabyte Ga-965P-DQ6.

I'll try and ping, and see what happends. Thanks everyone.

Will let you know.

---

### Post by carverj on 2007-08-27
To check your ip address, open the terminal window and type
ifconfig -a
to deactivate the interface try: 
ifconfig eth0 down
and then reactivate:
ifconfig eth0 up
so long as that is the interface connected and you want 
to automatically (or dynamically) assign an IP address to.

---

### Post by Pharisee on 2007-08-27
Just re installed Ubuntu. Realized that the connection issue occured even with the Live CD..

Thanks.

---

### Post by WebSiteGuru on 2007-08-27
> **conjur3r said:**
> What kind of motherboard do you have?  I only ask because some newish Gigabyte boards set the NIC into sleep mode after windows shuts down and linux cannot enable it.


Refering to his question, since you have a Gigabyte Ga-965P-DQ6. I think that there is the problem, not unless there is a way to tell it not to go to sleep. Also, you might be getting a speed issue. usually if you network is running at 100 you will need to force you network card to run and the same speed.

---

### Post by Pharisee on 2007-08-27
This is more complicated than when I had a 56k modem :P *If* the NIC is the issue, would putting one another one help resolve this issue? How would I get it to run at the same speed?

Cheers.

---

### Post by WebSiteGuru on 2007-08-27
> **Pharisee said:**
> This is more complicated than when I had a 56k modem :P *If* the NIC is the issue, would putting one another one help resolve this issue? How would I get it to run at the same speed?

Cheers.


Try looking in the BOIS setting. See if there is a LAN setting in the Integrated Peripherals.

---

### Post by Pharisee on 2007-08-27
Will do. Will post back here in the morning, thanks for all the help people :)

---

### Post by Pharisee on 2007-08-28
There is no settings in that regards. If I just install a second NIC would that do the trick?

Cheers.

---

