---
title: "Does ubuntu need a firewall"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-18
I know about firestarter, but will installing and enableing it increase my security to amazing standards, or is it a just a waist of time

---

### Post by Presto123 on 2007-12-18
Never a waste of time. ;)

This program is intended to increase security, so, if you feel that you need it, it never hurts to have it.

Firestarter seems to be a good choice, too. Pretty simple to set up.

---

### Post by Lostincyberspace on 2007-12-18
I don't use any wire wall and am fine. But I do reinstall all the time and change password etc.

---

### Post by coolbrook on 2007-12-18
I have a hardware firewall so it doesn't consume my resources.

---

### Post by Dapman01 on 2007-12-18
Consuming my resources isn't an issue for me.  I have a gaming PC and I don't game (anymore) in linux.  I use linux for everything except gaming so I wanted to put maximum security inside of it.  Besides a firewall, what else can I do

---

### Post by fatality_uk on 2007-12-18
Depends what your'e doing! IPTables are default in Linux so for general use, there's little need to apply a GUI front end such as FireStarter. However, if you have a need for P2P software or use some other software that requires a port or range of ports to be opened, then I would advise to install it and take full control.

A good guide is here [http://www.5dollarwhitebox.org/wiki/index.php/Howtos_Basic_IPTables]("http://www.5dollarwhitebox.org/wiki/index.php/Howtos_Basic_IPTables")

Ohh, forgot to add. If your using a router rather than a ADSL modem for instance, then that will usually have a hardware firewall. You can usually configure your ports from there if you don't want to add anything to Linux

---

### Post by Dapman01 on 2007-12-18
Can someone tell me the Ip address to access a belkin wireless router

---

### Post by stchman on 2007-12-18
> **Dapman01 said:**
> I know about firestarter, but will installing and enableing it increase my security to amazing standards, or is it a just a waist of time

Ubuntu already has iptables.  Firestarter is just a GUI to manipulate the iptables.  Also if you use a router then it also has a firewall.

---

### Post by Thelasko on 2007-12-18
Netfilter/IPtables is a firewall that is installed and active by default.  [Firestarter]("http://en.wikipedia.org/wiki/Firestarter_%28firewall%29") is just a nice interface for IPtables.  If you have problems with configuring your firewall then you should install Firestarter.  Otherwise you have the peace of mind of knowing that Ubuntu has it's firewall enabled by **default.**

---

### Post by fatality_uk on 2007-12-18
> **stchman said:**
> Ubuntu already has iptables.  Firestarter is just a GUI to manipulate the iptables.  Also if you use a router then it also has a firewall.

errr plagiarist :lolflag:

---

### Post by AnonCat on 2007-12-18
You should install firestarter just to aid in setting up iptables.  Once you load firestarter you'll want to choose "Preferances" and then "ICMP Filtering" and check mark the option to enable ICMP filtering.  After you do that you should be completely good.  Go to [www.grc.com](www.grc.com) and use their "shields up" site to test how secure your computer is after doing that.

---

### Post by LaRoza on 2007-12-18
I use a hardware firewall.

---

### Post by tech9 on 2007-12-18
> **LaRoza said:**
> I use a hardware firewall.

good choice... me too :)

---

