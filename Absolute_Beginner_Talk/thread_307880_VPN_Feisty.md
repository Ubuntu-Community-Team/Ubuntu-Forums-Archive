---
title: "VPN Feisty"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by sabrina on 2006-11-27
Hi all!

I have a problem installing the cisco vpn-client in feisty. I have to type in the path for the kernel headers in Feisty, but I don't know, where they are. They are not in /usr/src/

---

### Post by steve.horsley on 2006-11-27
Use synaptic and search for linux-headers. In Edgy, my exact package is linux-headers-generic. It installs files in /usr/src.

You may also need to install build-essential package which includes a compiler, build utilities etc.

---

### Post by sabrina on 2006-11-29
Thanks for the answer.

What do I type as path then? Only /usr/src?

---

