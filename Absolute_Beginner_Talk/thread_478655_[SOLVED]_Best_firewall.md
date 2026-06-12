---
title: "[SOLVED] Best firewall?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by neptune229 on 2007-06-19
I am running Xubuntu 7.04 with an 800MHz Celeron processor w/128 MB of RAM. Does anyone have a suggestion for a lightweight firewall I could use?

---

### Post by skymera on 2007-06-19
there is no need for a firewall.

but firestarter is a nice one.

---

### Post by Crafty Kisses on 2007-06-19
> **neptune229 said:**
> I am running Xubuntu 7.04 with an 800MHz Celeron processor w/128 MB of RAM. Does anyone have a suggestion for a lightweight firewall I could use?

You don't get viruses with Linux. :D

---

### Post by angryfirelord on 2007-06-19
Still, while the majority of ports are closed on Linux distros, it's certainly not 100% hack-proof. Firestarter is what I use.

---

### Post by skymera on 2007-06-19
he was after firewall, not anti-virus :)

---

### Post by oilchangeguy on 2007-06-19
> **skymera said:**
> there is no need for a firewall.

but firestarter is a nice one.

ubuntu has a built in firewall. it's called iptables. firestarter is simply a gui for iptables, not the firewall itself.

---

### Post by oilchangeguy on 2007-06-19
> **Codename said:**
> You don't get viruses with Linux. :D

wrong. you can. it's very hard, but it can be done.

---

### Post by ugm6hr on 2007-06-19
> **neptune229 said:**
> I am running Xubuntu 7.04 with an 800MHz Celeron processor w/128 MB of RAM. Does anyone have a suggestion for a lightweight firewall I could use?

What everyone is trying to say is that (X)ubuntu keeps all incoming ports closed as default (with the default firewall iptables), so there is no need for a "firewall" unless you want to either open incoming ports (e.g. for torrent use etc), or want to block outgoing ports.

If you are looking for an easy way to edit these controls - Firestarter is available from Synaptic Package Manager.

---

### Post by Crafty Kisses on 2007-06-19
> **oilchangeguy said:**
> ubuntu has a built in firewall. it's called iptables. firestarter is simply a gui for iptables, not the firewall itself.

Ubuntu is neat. :KS

---

### Post by phr0ze on 2007-06-19
> **Codename said:**
> Ubuntu is neat. :KS

What is the point of this post?

Don't get a firewall. The provided IPtables are enough. Especially with that limited hardware.

---

### Post by Crafty Kisses on 2007-06-19
> **phr0ze said:**
> What is the point of this post?

Don't get a firewall. The provided IPtables are enough. Especially with that limited hardware.

Sorry for having a sense of humor.

---

### Post by angryfirelord on 2007-06-19
Not everybody knows iptables and firestarter is relatively lightweight.

---

### Post by oilchangeguy on 2007-06-19
> **angryfirelord said:**
> Not everybody knows iptables and firestarter is relatively lightweight.

firestarter is NOT a firewall. is a gui for iptables. nothing more!

---

### Post by angryfirelord on 2007-06-19
> **oilchangeguy said:**
> firestarter is NOT a firewall. is a gui for iptables. nothing more!
I know that, but like I just said, not everyone wants to configure iptables by hand, so firestarter helps take care of that.

---

