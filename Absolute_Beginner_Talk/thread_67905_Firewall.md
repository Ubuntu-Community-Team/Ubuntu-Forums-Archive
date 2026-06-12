---
title: "Firewall"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by canadianwriterman on 2005-09-21
Does Breezy have a built-in firewall? Does anyone recommend that I install one, if it doesn't? Thanks for your help.

---

### Post by GoA on 2005-09-21
Yes, linux has a firewall build into a kernel. The difficult way to modify this is through the iptables. The easy way is to install firestarter program from the repositories which is a very easy using GUI for iptables. And after you have the configured the iptables with firestarter, you can just close it and let the iptables to do their work.

EDIT: This is also in hoary. Iptables has been build in kernel since 2.4 versions if I remember correctly.

---

### Post by az on 2005-09-21
Whether you need one or not depends on your needs.  I wouldn't bother with one.  But is you VPN, ssh or VNC in and out of your house or run some foreign software, then I would consider it.

I think firestarter is pretty good...

---

### Post by canadianwriterman on 2005-09-21
Thank you, both. I do have a DSL connection. I'll take a look at Firestarter.

---

