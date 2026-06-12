---
title: "Blacklisting TI module"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by HarshReality on 2007-07-01
As I understand the TI module for SD Readers is default active.. I have a card reader however it is NOT TI so the module is loading and causing me fits. I'd just like to know how to blacklist the sucker to keep it from loading or remove it without having to recompile a kernel (process here is still shakey to me on compile).

Assist is greatly appreciated.

R

---

### Post by annda on 2007-07-01
you need to create a new file in /etc/modprobe.d/ its name should start with "blacklist" and the contents should be

> blacklist modulename

for example if the module is ti, you could have a file /etc/modprobe.d/blacklist-ti that has the line:
> blacklist ti

---

