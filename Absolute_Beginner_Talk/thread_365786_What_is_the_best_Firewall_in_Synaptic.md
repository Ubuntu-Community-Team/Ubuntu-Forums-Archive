---
title: "What is the best Firewall in Synaptic?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-20
What is the best firewall in Synaptic? Open for opinions. Please state why you prefer the one you are using. Thanks for all replies. :)

---

### Post by Madpilot on 2007-02-20
The standard Linux firewall is called "iptables"; it's included in Ubuntu by default. The standard front-end for it is called Firestarter - it's got a nice interface and a bunch of ways to make configuring your firewall & 'net connections easier.

Note that by default, you don't really need to worry about the firewall in Ubuntu; unlike XP, there are no active services in a default Ubuntu install. Nothing is going to phone home without asking you for permission first.

Firestarter is great for setting up connection sharing, though. I used this a while ago to let a visiting laptop use a crossover cable & my tower's 2nd ethernet port to connect to the web, because I don't have wireless and my router was packed in a box somewhere.

---

### Post by IronMac on 2007-02-20
+1 on the above advice.  :)

---

### Post by ramjet_1953 on 2007-02-20
The firewall is built-in.

Just download firestarter, using Synaptic package manager.

It is a graphical way to alter the iptables to suit yourself and to monitor the nasties trying to get into you system.

Regards,
Roger 8)

---

### Post by kittyhawk63 on 2007-02-20
Thanks for the information. I shall follow the advice. :)

---

### Post by Maestro23 on 2007-02-20
> **kittyhawk63 said:**
> Thanks for the information. I shall follow the advise. :)

Here is the Firestarter website, so you can read all about it: [http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by kittyhawk63 on 2007-02-20
Thanks again to you all. Morning Maestro23.

---

### Post by drphibes52 on 2008-01-23
> **kittyhawk63 said:**
> What is the best firewall in Synaptic? Open for opinions. Please state why you prefer the one you are using. Thanks for all replies. :)

I am currently experimenting with Lokkit which is another front end for iptables in Ubuntu.

It is more straight forward to use for the novice user. It asks questions, then sets up the firewall accordingly. It is much easier to properly set up than Firewall.

I recommend Lokkit for novice users and Firestarter for advanced users.

---

