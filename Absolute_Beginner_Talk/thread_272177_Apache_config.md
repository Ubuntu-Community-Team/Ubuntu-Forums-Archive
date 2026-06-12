---
title: "Apache config ?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by nigelicious on 2006-10-05
Sorry for the noobness that shall follow :

I used apt-get to install apache and followed the guide on the ubuntu-wiki..
Set NAT on my modem/router to port forward port 80 to that particular pc. Webpage loads fine on pc's in internal network using  both the local ip address (10.1.1.3) aswell as dyndns address i have for my ip. However from work and a couple of other friends machines, it will not load.
Is there something I could be missing from the conf file that is not there by default/from ubuntu wiki?

---

### Post by robinl on 2006-10-05
Change your router configuration to something like 81, traffic may be directed to the configuration page but wasn't allowed to see it and thus will not load. If it doesn't work enable DMZ as it will open every single port to your computer.

PS: what do you mean by the dyndns address? From an internal network the dyndns address (***.dyndns.org etc.) and your external IP should not work.

---

### Post by nigelicious on 2006-10-05
Yes, I have a *.dyndns.org address that points to my home network ip, and I have the router forwarding through the ports required to the ubuntu box (ie ssh, ftp, port 80 for apache).
So pointed my web browser to either 10.1.1.3 or blahblah.dyndns.org both were successful in showing the page from the different boxes on my home network. But externally, no go.

---

### Post by robinl on 2006-10-05
Well your ddclient is not configured correctly. It is reporting internal IP instead of external IP which is why typing in *.dyndns.org works from internal network when it shouldn't. I forgot how to configure it to report your external IP address but a search on the forums should do the trick.

---

