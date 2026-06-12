---
title: "How to use Terminal Server client?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by vpit on 2007-04-21
I am quite familiar with using the rdp client in winows and the ts client in fiesty looks the same, however when I try to connect to my windows 2003 box using either the hostname or ip I get errors.  When I use the ip address 192.168.1.104 it says NO ROUTE TO HOST.  Any suggestions?

---

### Post by yeleek on 2007-04-21
forget ubuntu for now... From the sounds of that i'd check your basic network connectivity.

i.e. do you have a route through to that address (and forget the name resolution as well for now)

ping/tracert/etc - if it can't tracert to the server then rdp won't work :)

---

### Post by vpit on 2007-04-21
Ok, I assumed becuase I am able to browse files on a windows share on that box that name resolution would not be an issue.  I just tried opening terminal and pinging 192.168.1.104 and it does not ping...?

---

### Post by yeleek on 2007-04-22
That doesn't make sense to be honest - if you can browse files from ubuntu to your windows 2003 box either via the C$ share or another share, then you should be able to ping it at least.  Unless of course you've got firewall rules setup at either end?

---

