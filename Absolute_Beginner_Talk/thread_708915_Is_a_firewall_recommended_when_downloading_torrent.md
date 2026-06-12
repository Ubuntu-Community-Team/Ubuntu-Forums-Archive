---
title: "Is a firewall recommended when downloading torrents"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by rbrittner on 2008-02-26
Ok so I've read and have been using Firestarter as a firewall.  Is it really necessary or can I get rid of this.  I've read some posts saying to use it and some saying it's not worth it?  any ideas?

---

### Post by taurus on 2008-02-26
Firestarter is not a firewall.  Iptables is and it is running as a default when you boot Ubuntu.  You use firestarter to configure your firewall.  So in reality, you don't need to use/run firestarter if you don't want to.

---

### Post by PeterJS on 2008-02-26
The idea of torrents is that they are peer to peer so to get anything transfered you need to open and allow lots of connections to seemingly random ip addresses (the peers in the swarm). Having a firewall that would block them seems counter productive, no?

---

### Post by rbrittner on 2008-02-26
ok, so basically firestarter is just a GUI for iptables then.

---

### Post by spook1980 on 2008-02-26
firewalls, anti-virus software, & antispyware are not necessary in Linux.

---

### Post by northern lights on 2008-02-26
Oye,

first of firestarter is not exactly a firewall- it's just a GUI for "iptables" the Ubuntu in-built firewall. There are several such GUIs out there.

I personally see no use for it, since I am sitting behind a well configured router. I dunno if that applies to your network. Also I don't download torrents. But I'd say the probability of running into something malicious that woulda really hurt you without iptables and doesn't with is rather slim. Possible dangers are best decreased by choosing what sites you visit and where you download from reasonably.

---

### Post by 3rdalbum on 2008-02-26
If you're downloading torrents on an ordinary desktop machine without extra services running, you don't need a firewall.

---

