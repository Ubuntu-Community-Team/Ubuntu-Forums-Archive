---
title: "How secure is a system without a router, i.e. direct connection to DSL"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by TdS3Tm on 2007-09-14
I have read lots of posts about security. My question is still not addresed. How secure is it to connect directly to the internet with no router? I assume that Ubuntu Iptables is the only security in place. What risks and vunerabilities am I open to? Any feedback would be appreciated.

---

### Post by marco123 on 2007-09-14
It depends what you use the computer for.  As long as you aren't running any services which require open ports then you are about as secure as you can be with an operating system.  No ports are open by default on a fresh install of Ubuntu.

---

### Post by marco123 on 2007-09-14
I should also add that there are no services listening on open ports as well.  A port scan with NMap or at - [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)  will show no open ports.

---

### Post by DM was on fire! on 2007-09-14
And if you are, you should be able to install FireStarter, a firewall for Linux. ^^ It's probably in your repositories somewhere, but I don't believe it's installed by default on Ubuntu.

---

### Post by PmDematagoda on 2007-09-14
Excuse me for asking a very noobish question, but what differences are there between an internet connection through the router and a direct one?

---

### Post by marco123 on 2007-09-14
> **DM was on fire! said:**
> And if you are, you should be able to install FireStarter, a firewall for Linux. ^^ It's probably in your repositories somewhere, but I don't believe it's installed by default on Ubuntu.

Also Firestarter, properly configured, will stealth all your ports.  I usually end up turning it off when I'm downloading a torrent though.:)

---

### Post by marco123 on 2007-09-14
> **PmDematagoda said:**
> Excuse me for asking a very noobish question, but what differences are there between an internet connection through the router and a direct one?

Routers nowadays have hardware firewalls built in I think.

---

### Post by SOULRiDER on 2007-09-14
Most routers have a firewall. I myself used a DSL connection without a router for many years and never had a problem, in fact, the firewall in my router is deactivated at the moment... im not a very security conscious person though.... Firestarter can be sued as a firewall, it doesnt come installed by default but its in hte repositories.

Check this link out.
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

If youre using KDE you might wanna try KguardDog.

---

### Post by stchman on 2007-09-14
> **TdS3Tm said:**
> I have read lots of posts about security. My question is still not addresed. How secure is it to connect directly to the internet with no router? I assume that Ubuntu Iptables is the only security in place. What risks and vunerabilities am I open to? Any feedback would be appreciated.

The iptables should protect you as Ubuntu has all ports stealthed by default.

I do recommend a router as it gives you far more functionality and allows you to connect multiple PCs to your connection.  Routers are really cheap and can be had for around $20.

---

### Post by n3tfury on 2007-09-14
> **DM was on fire! said:**
> And if you are, you should be able to install FireStarter, a firewall for Linux. ^^ It's probably in your repositories somewhere, but I don't believe it's installed by default on Ubuntu.

if i'm not mistaken, Firestarter is actually just a front end GUI for iptables.

---

