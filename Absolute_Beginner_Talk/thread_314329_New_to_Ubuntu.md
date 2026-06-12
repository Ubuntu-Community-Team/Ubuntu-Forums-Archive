---
title: "New to Ubuntu"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Kevin Clark on 2006-12-07
I am downloading Ubuntu 6.10 for servers.  I want to setup a box that will be between our internet modem and our router.  Here is my situation.  I have blocked myspace successfully using the filters on our router.  Those that are trying to access myspace have found out about proxy services.  In particular, they are using hidebehind.net.  I haven't been able to block out these proxy services.  I am hoping that Ubuntu and firewall software will help.  Has anyone done a setup like this?  From what I have read so far, firestarter is best for a firewall.  I am very new to all of this, but I am willing to learn to keep people from accessing myspace at work.  I am scared to death about setting this up especially since I know nothing about command lines.  Does anyone have any advice for setting this up?  Thanks in advance.

---

### Post by skmassey on 2006-12-07
Unfortunately I don't think I have much good news for you.  The good news is that you can probably block myspace using an ubuntu firewall...the bad news is you probably aren't going to be able to do it with a GUI tool like firestarter.  Although firestarter is great for individual machines as a frontend for IPtables, for any complex configuration it is best to edit the IPtables configuration yourself and define a set of rules that way.  There are many good how-to's online for IPtables and *nix firewalls.  Personally, I would use a BSD for a firewall because of the security of the system and the fact that PF is great.  I'm including a link to a book on both IPtables and PF.  They provide good reading and hopefully more insight into what you're going to be dealing with.  Good Luck and don't let my comments turn you away from Ubuntu, I personally prefer PF to IPtables.

[http://debian.yaako.org/books/%5bebook%5d%20IpTables%20Tutorial.pdf](http://debian.yaako.org/books/%5bebook%5d%20IpTables%20Tutorial.pdf)

[http://debian.yaako.org/books/How%20to%20Build%20a%20FreeBSD-STABLE%20firewall%20with%20IPFILTER.pdf](http://debian.yaako.org/books/How%20to%20Build%20a%20FreeBSD-STABLE%20firewall%20with%20IPFILTER.pdf)

---

