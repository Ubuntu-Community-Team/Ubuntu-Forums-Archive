---
title: "Disable Internet on File Server"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by nomad1970 on 2007-11-21
Hi,

Quick question.  Ubuntu 7.10 Server, being used only as a file server.   After doing the necessary software installs / updates, I don't need it to have any access to the internet - for security reasons.

What is the easiest way to do this, install a firewall that allows 0 incoming traffic, or just edit out the gateway in interfaces config?

Thanks!

---

### Post by finer recliner on 2007-11-22
fyi:  ubuntu comes with a firewall called iptables which has all of you ports turned off by default. you can verify this by using a port scanner on yourself (nmap is a good one).

if you want more control over the firewall, i recommend installing a GUI interface for iptables (most will recommend firestarter) since iptables is difficult to work with in the terminal.

---

