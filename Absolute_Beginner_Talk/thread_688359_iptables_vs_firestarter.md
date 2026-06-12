---
title: "iptables vs firestarter"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-02-05
which is better to use for a firewall solution in terms of ease of use, functionality, reliability, performance etc- iptables or firestarter?  i have read that iptables is a script-based firewall (no GUI) while firestarter is a GUI-based solution.  thanks.

---

### Post by Nythain on 2008-02-05
iptables IS your firewall... and is usually blank untill access by something, usually, tada, FireStarter... wich is nothing more than a fancy gui interface to iptables, making life a lot easier with a cilck of a few buttons.

moral of the story, if you want to learn the hard way of doing things, google the hell out of iptables... if you are lazy, install firestarter... but dont assume firestarter is a firewall, just a pretty front end for the already existing from the get go iptables

---

### Post by HemiGTX on 2008-02-05
Firestarter is a gui application to let you set the iptables. Firestarter is not a firewall itself.

---

### Post by ruy_lopez on 2008-02-05
Firestarter is a front-end for iptables. The only difference between using firestarter and configuring iptables manually is ease of use. Since they both use the same underlying filtering, there isn't any difference in performance or reliability etc.

Check out FWBuilder too.

---

### Post by Matt26 on 2008-02-05
thanks for the info- fyi, labelling firestarter a firewall wasn't an assumption, this was merely the understanding i came away with after reading info on the program from both it's website and other posts online.  is iptables installed by default on ubuntu 7.10 or does it have to be installed manually?

---

### Post by HemiGTX on 2008-02-05
Ip Tables is installed by default

---

### Post by Seisen on 2008-02-05
Iptables is part of the base programs installed by default in Ubuntu. A lot of people assume  firestarter is a firewall, me included when I first started using Ubuntu, so I do agree with you on that aspect.

---

### Post by hyper_ch on 2008-02-05
I daresay you don't need to configure iptables at all...

---

