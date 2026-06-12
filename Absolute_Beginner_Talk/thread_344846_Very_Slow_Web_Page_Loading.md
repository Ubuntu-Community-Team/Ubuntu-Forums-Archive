---
title: "Very Slow Web Page Loading"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Philber on 2007-01-23
Ok, I have another problem with my brand new Ubuntu 'deployment'. I am of course using Firefox to load and render web pages but am finding that each page is very slow to come in/render on screen

This is not a computer hardware problem, the machine itself opens programmes and generally works fast with Ubuntu, but it seems there's a problem pulling pages off the net

I have a home network with four other computers, all Macs, and there is no problem with any of them

My Internet service is NTL cable, and I connect everything through a 3Com wired/wireless router. The Ubuntu machine is connected via Ethernet

Any ideas anyone?

I have done the updates by the way, and this has made no difference even after a re-start

Philber

---

### Post by taurus on 2007-01-23
It's because of your graphic card.  You need to install a driver for it.  You already have another thread with a similar problem.  Why not use that same thread?

---

### Post by Philber on 2007-01-23
I had no idea the matters were related!

---

### Post by taurus on 2007-01-23
Paste the output here.

```
lspci
```

---

### Post by Philber on 2007-01-23
Thanks for your help. I'm going to have to do this tomorrow as I am not able to get on the machine in question at the moment. I am writing to the forums now on my MacBook Pro

---

### Post by PaulFXH on 2007-01-23
I had the same problem when I tried Firefox first in Ubuntu. Luckily, in my case, it was very easy to resolve.
Just type about:config in the address box and then put ipv6 in the filter box.
The value for network.dns.disableIPv6 should be set at** true**. If it's set at **false**, just toggle it to **true** and try Firefox again.
For me, this simple procedure boosted the speed enormously.

---

### Post by Philber on 2007-01-25
Thanks PaulFXH, the ipv6 thing was the answer. Just double-clicking the item in the filter box changed the setting, and things are now fine. Thanks again

---

