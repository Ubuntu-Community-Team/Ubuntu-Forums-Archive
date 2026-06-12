---
title: "Need Help with Linksys WUSB54G Adapter"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Hastings101 on 2008-04-05
I just switched to Ubuntu today (after using my friend's for a few  weeks; decided I liked it more than I do windows) but cannot get my wireless internet to connect. 
      I have a Linksys WUSB54G (v4) Adapter that seems to be working as I can see other networks to  connect to, but I cannot connect to any of them.  How can I get my Adapter to connect?

---

### Post by cifdtruckie on 2008-04-05
I had the same issue when I switched over, and it seems to be a common problem.  As of yet, there is no true support of USB wireless adapters for Ubuntu.  You could try ndiswrapper to install the windows drivers...
```
sudo apt-get -install ndiswrapper
```
...but I can tell you firsthand that that option never worked properly for me. 

 If you have a free PCI slot, I'd highly recommend going with a PCI wireless adapter.  Get one with a Realtek chipset (I picked up a generic one for about $30 and it worked right out of the box with absolutely no tinkering) and you'll save yourself a huge headache!

---

