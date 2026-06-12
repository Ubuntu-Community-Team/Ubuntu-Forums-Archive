---
title: "VNC into my Ubuntu problem ..."
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-02-13
I have Ubuntu 6.10 at home and would like to VNC from work into my home PC.  I can VNC into Ubuntu from another PC on the LAN at home but have not been able to from work.

I have a router and have opened up ports:

TCP and UPD 5900-5909
TCP and UDP 5800-5809
TCP and UDP 5500-5509
TCP and UDP 6000-6009

Are there another ports that need to be opened?

I can Remote Desktop into a Windows XP PC at home -- could it be that my work router is blocking access on the VNC ports?  If so, can VNC be configured to use the same ports as Remote Desktop (i.e. 3389)?

Thanks  

Carl

---

### Post by carlosfocker on 2007-02-13
Most IT department will definitely block remote desktop connection via a firewall. The place I work now does it and I did it as a system admin at my last job. You can try connecting your computer directly to your modem (I know this is technically the wrong word) and try again.  It would definitely take your router out of the equation ;)

---

