---
title: "Wireless USB Adapter question"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by TarB on 2007-07-26
I have a Linksys Wireless-G USB Adapter, and I was running airodump in order to sniff network and there was a problem. It is very very slow, for example for a particular network I will be like if I get 10 packets an hour.. Is that because my wireless adapter sucks, and it is too weak, since those network's signal strength is pretty low? Or am I not understanding something?

---

### Post by Mark_in_Hollywood on 2007-07-26
I suggest posting this over at Networking & Wireless forum, rather than beginner, even though you have but 5 beans.

What driver are you using? 

you need to post the outputs of:

lsusb

sudo lshw -C network

and we can go from there. I just learned how to install a Linksys WUSB11v4 so it's somewhat fresh in my mind.

---

