---
title: "Network Problem"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Mark1948 on 2007-06-09
I almost have Linux running :) LOL

I am trying to install this on a laptop with a X1600 graphics card and so i need the fixes. Anyway when I went through the install I wasn't aware of this so I selected don't configure the network now, oops!!! Now I need the fixes of the net :(

So the question is how do I config the network from the command prompt?

---

### Post by sandwitch on 2007-06-09
if your graficall user interface is up, just go to System => Administration => Network
else you have to fill in "/etc/network/interfaces" edit it with nano or vim.
if you use dhcp then its simple :
# The primary network interface
auto eth0
iface eth0 inet dhcp
Should do the trick
else:
address xxx.xxx.xxx.xxx
network xxx.xxx.xxx.0
netmask 255.255.255.0
gateway xxx.xxx.xxx.xxx
these settings depends on your network conguration.
this looks like a good startpoint [http://textsnippets.com/posts/show/319](http://textsnippets.com/posts/show/319) 
thanx to bcrow
good luck :)

---

