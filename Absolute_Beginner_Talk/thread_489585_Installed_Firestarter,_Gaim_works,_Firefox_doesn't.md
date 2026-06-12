---
title: "Installed Firestarter, Gaim works, Firefox doesn't"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-07-01
I installed the Firestarter firewall.  It automatically allowed Gaim to connect to the internet, but I cannot load anyweb pages on Firefox.  Any help on how to enable different programs to use the internet?  Help is much appriciated thank you!

---

### Post by mendingo84 on 2007-07-01
does you firewall forward the port 80?

---

### Post by fontenot_1031 on 2007-07-01
I'm not for sure how to do that.

---

### Post by mig5 on 2007-07-01
See if this works:
Go into firestarter, click the policy tab, on the editing tab change to outbound then click permissive by default.

---

### Post by mendingo84 on 2007-07-01
i don't have Firestarter installed...but there should be some menu where the ports allowed are listed. make sure that the one 80 is in there.

---

### Post by fontenot_1031 on 2007-07-01
Under Inbound policy I have allowed port 80 for everyone and the bit torrent ports for everyone.  Firefox still doesn't load, I haven't tried bit torrent though.

---

### Post by fontenot_1031 on 2007-07-01
> **mig5 said:**
> See if this works:
Go into firestarter, click the policy tab, on the editing tab change to outbound then click permissive by default.

Hmm that doesn't seem to work either.

---

### Post by mendingo84 on 2007-07-01
yeah...if want to browse, than it's outgoing traffic ;), not Inbound

---

### Post by fontenot_1031 on 2007-07-01
Oo oh.  I clicked the events tab and clicked reload, now Gaim doesn't work either.

---

### Post by mig5 on 2007-07-01
Go to the policy tab again, select inbound policy this time, right click on the 2nd white area, add rule, put in port 80.

---

### Post by Malibu Illusion on 2007-07-01
> **mig5 said:**
> Go to the policy tab again, select inbound policy this time, right click on the 2nd white area, add rule, put in port 80.

You do not need to allow inbound traffic on port 80 unless you're running a http daemon.  This will do absolutely nothing for web connectivity.

In order to connect, you need to set your "outbound" policy to "permissive by default" and you need any router firewall that you're connecting through to be correctly configured to allow outbound connections from any TCP port on your computer to port 80 of external web servers.  

You may also wish to turn off IPv6 in Firefox, which has been known to cause connectivity issues.  To do this:

**1: ** Type "about:config", without the quotes, into the Firefox address bar.

**2: ** Type "v6", without the quotes, into the filter box.

**3: ** Toggle "network.dns.disableIPv6" to "true."

Take care.

---

