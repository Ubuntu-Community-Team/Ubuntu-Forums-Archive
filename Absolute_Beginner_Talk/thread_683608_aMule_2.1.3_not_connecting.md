---
title: "aMule 2.1.3 not connecting??"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by tylerdurden15 on 2008-01-31
As the title states i just downloaded aMule and it refuses to connect.  I looked at prior posts here about adding servers but that didn't  help.  Any clues?  Otherwise i am just going to remove it.

Thanks!

---

### Post by emarkd on 2008-01-31
Could be a firewall issue.  By default Ubuntu has no open ports, so your p2p peers can't connect.  A good gui firewall controller is called Firestarter and it's in Synaptic.  Have you tried installing something like this and opening the appropriate ports?

---

### Post by tylerdurden15 on 2008-01-31
No i havn't i will try that now thanks!

---

### Post by tylerdurden15 on 2008-01-31
Its still doing it saying no servers found in valid server list, is there anything i should be doing in firestarter? or any other suggestions?

---

### Post by emarkd on 2008-01-31
Yeah, you have to open the ports.  In Firestarter, click on the policy tab and select to edit the Inbound Traffic Policy.  Then add a rule to open the proper ports.  I don't use aMule so I don't know what those ports are, though.  I would imagine aMule would tell you  somewhere...

---

### Post by Hallvor on 2008-01-31
The aMule ports are under Preferences in aMule.

You don`t have to install Firestarter to open ports. You can do it just as easy with the command line.

Check my signature.

---

### Post by gandaran on 2008-01-31
> **tylerdurden15 said:**
> As the title states i just downloaded aMule and it refuses to connect.  I looked at prior posts here about adding servers but that didn't  help.  Any clues?  Otherwise i am just going to remove it.

Thanks!

paste this url ( [http://www.gruk.org/server.met.gz](http://www.gruk.org/server.met.gz) ) the one on amule is outdated, it won't connect.
you don't have to open any ports unless you installed firestarter and blocked the ports (ICMP enabled) then open the edonkey server port 4662 in the firestarter

---

