---
title: "[SOLVED] aMule"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-21
hello,

could anyone tell me what I should do to get aMule work? (I'm on Ubuntu Gutsy). When I click on "connect" it tells me "no valid servers found in the server list". The "preferences" option is a bit confusing when it comes to servers/connections...

thanks.

---

### Post by maddog39 on 2008-03-21
Well I've honestly never used aMule so I really cant help you there. Although some other p2p applications that I find work really well under ubuntu in particular. You might want to take a look at [Frostwire]("http://www.frostwire.org/") (download the .deb from their website, its not in the repository) or Gtkgnutella. When I went to take a look at the aMule website, its seems that it hastn been updated in quite a while and could be a dead project which is maybe why it wasnt working for you.

---

### Post by gandaran on 2008-03-21
you have to change the url for a new one
try this one:
[http://www.gruk.org/server.met.gz](http://www.gruk.org/server.met.gz)
then click the servers button to download a new list of servers

if you have the firestarter firewall instaled, open the 4662 port.

---

### Post by annda on 2008-03-21
you must have an old/deprecated server list. it happened to me too with an older version of aMule. i would suggest trying to  add a working server to servers list in Networks

manual server add:

Name: eDonkey Server No1
IP: 77.247.178.244
port: 4242

---

### Post by al.adab on 2008-03-22
thanks both. the eDonkey server solution worked.

---

### Post by Hallvor on 2008-03-24
> **maddog39 said:**
> Well I've honestly never used aMule so I really cant help you there. Although some other p2p applications that I find work really well under ubuntu in particular. You might want to take a look at [Frostwire]("http://www.frostwire.org/") (download the .deb from their website, its not in the repository) or Gtkgnutella. When I went to take a look at the aMule website, its seems that it hastn been updated in quite a while and could be a dead project which is maybe why it wasnt working for you.

How could it *not *be evident that aMule is in active development if you visited the aMule website?

[http://www.amule.org/](http://www.amule.org/)

There are even debs for the aMule 2.2.0 CVS version built for Ubuntu.

---

