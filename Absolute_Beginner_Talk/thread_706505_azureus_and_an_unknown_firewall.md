---
title: "azureus and an unknown firewall"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by K_Boomer on 2008-02-24
Ok, I even tried to do some research on this issue.... to no avail.

Here's the problem:
Yellow smiley on azureus, terrible speeds (250bps or 3 kbps...), and no understanding of the esoteric lingo that everyone uses to describe how to fix the problem. Also, parts of azureus are in a foreign language. Don't know what language, but it uses a different alphabet that I cant decipher.

Im pretty sure I have an NAT problem, but I dont know how to configure my firewall to accept certain ports. My internet connection is cable based and from a university with a heavy firewall. I have tried changing ports in azureus to the recommended safe ones, but that is all I feel comfortable doing so far (no idea how to check ip-tables). Whenever I try to relate to other online articles, I end up making assumptions and screwing my computer up WAAAAAY worse. I would love it if someone could walk me through resolving this issue.

Please dont post a site that generalizes these issues into one resolution. Chances are I've checked them out already and they made less sense than a coked out George W. Bush.

I am using ubuntu gutsy.

---

### Post by Beefeater on 2008-02-24
You could try and install firestarter and open the port there.
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

Are you behind a local router as well?

---

### Post by richaoj on 2008-02-24
also , you said that you were in a university setting.  are you sure the college is not blocking torrents?  you could also try going into the settings, i'm not sure where it is in azureus, but there are places you can go to encrypt your connections.  (If i remember correctly the option is "prefer to encrypt data" or something like that)  also, there is a nat/firewall test tool in azureus.  have you run this? does it say OK, or does it say NAT error??  if you have not messed with the firewall settings in Ubuntu, that should not be the problem.  but if you have installed firestarter or some other firewall, you will have to mess with the settings in there.  but i don't think it is necessary to do so.

---

