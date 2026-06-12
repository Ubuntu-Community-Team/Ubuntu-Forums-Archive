---
title: "Azureus on feisty- sorta how to"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by jdawdy on 2007-05-03
I beg everyones pardon for the utter patheticness-ness of this posting.  Lack of time!

Installed Java from Suns website, installed Azureus via synaptic on Feisty.  

Runs fine, but no transfers take place.  Router has the ports open (49996), and it works fine on my dual-boot laptop with Windoze.
 
Search around on internet and see I need to issue a iptables command line command to open the requisite ports.

This does *NOT* work.  Appears there may be some bug in iptables in feisty.  

I download Firestarter firewall program.  Run azureus, and Firestarter blocks the connection.  I click on the policy tab in firestarter to edit policy to "Allow service on port 49996 for everyone".

Azureus now works fine.

Jim

---

### Post by pay on 2007-05-03
So the problem is fixed?

---

