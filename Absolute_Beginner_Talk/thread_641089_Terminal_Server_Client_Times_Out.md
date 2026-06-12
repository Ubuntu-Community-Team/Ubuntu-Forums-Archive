---
title: "Terminal Server Client Times Out"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by dgoodma on 2007-12-15
I have installed the tsclient, trying to connect to a Windows XP machine on my home network.
I enabled Remote Desktop on the Windows Machine
I added to the firewall on my router
I can ping the Windows machine.
Have tried connecting with name, fully qualified name, IP address.

The client errors saying the connection timed out.

What else needs to be configured?

I have used this successfully on a Linux PC at work connecting to Windows 2003 servers, works great there.

---

### Post by mellowd on 2007-12-15
You sure port 3389 has been opened? RDP uses port 3389

---

### Post by dgoodma on 2007-12-15
Thanks, that was it. In addition to a Firewall on my router, I had one on the PC that had to be opened to that port.

And, I had never setup my PC with other than the account that came with it, it did not have a password, so it would not allow the tsclient to connect to it until it had a password.

---

### Post by mellowd on 2007-12-15
Great to hear! :)

---

