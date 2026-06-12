---
title: "installing ndiswrapper &amp; WUSB11v4"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by scotty76uk on 2006-10-31
Ok

From my understanding ubuntu 6.06 does not come with ndiswrapper preinstalled. For me this is a good thing

I have a linksys WUSB11v4 wireless Lan stick

I have ploughed through the forums and have found that I need to install the most upto date version of ndiswrapper to have any hope of using this hardware.

I have downloaded this and have the file "ndiswrapper-1.28.tar"

I have also downloaded the most upto date drivers for my WUSB11v4

My first problem is how to install ndiswrapper from this file what I can see it is not as straight forward as normal applications

Do I need to copy this file to anywhere perticular, and then what, I'm at a loss

---

### Post by faraazs on 2006-10-31
The standard install procedure should work fine:

get the essential build tools, so open a terminal and type in```
sudo apt-get install build-essential
```
navigate to the directory and type in```
make
```and then type```
sudo make install
```that should do it.

---

### Post by scotty76uk on 2006-10-31
thanks for your reply

do I have to copy the ndiswrapper file anywhere perticular?

its on a spare drive at the moment

---

