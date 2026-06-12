---
title: "Trouble with Wireless on Kubuntu"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-11-06
I just installed Kubuntu Edgy on my family's desktop computer, but I can't figure out how to connect to the Internet on it. I went to the network options and the wireless connection is shown there, so I turned it on and told it to connect to Cyberton (the ESSID of my network) and I gave it the WEP key, but it refuses to connect.

---

### Post by wieman01 on 2006-11-07
When you run this command from command line, is there any output?
> iwlist scan
If so post it.

The also the contents of this file:
> sudo gedit /etc/network/interfaces
I think you're close.

---

