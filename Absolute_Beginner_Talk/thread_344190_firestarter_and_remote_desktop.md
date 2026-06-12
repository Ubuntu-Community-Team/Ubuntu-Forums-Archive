---
title: "firestarter and remote desktop"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by getaboat on 2007-01-22
I am using Remote desktop (RDPv5) to remote desktop to a Windows box over a VPN (vpnc) connection.

Firestarter had the default settings for outgoing but unless I stop firestarter my RDP session doesn't start apparently blocked silently by firestarter, 

I had rather hoped that netstat might give me a clue what was going on when RDP fires up but
none the wiser. 

If you know the answer great, otherwise what tools should I be using to see what firestarter is trying to block (not in the logs from what I can see)?

Getaboat

---

### Post by scrooge_74 on 2007-01-22
You can configure firestarter to allow incoming connections or services you requiere

---

### Post by getaboat on 2007-01-22
What tools can I use to find out what I need to configure in firestarter for RDP?

Getaboat

---

### Post by scrooge_74 on 2007-01-22
you should open firestarter and go to the rule taps and start configuring which ports you want open and from where do you want to connect

---

