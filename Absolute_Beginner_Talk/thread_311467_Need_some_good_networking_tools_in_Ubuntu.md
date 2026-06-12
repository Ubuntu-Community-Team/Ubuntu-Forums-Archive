---
title: "Need some good networking tools in Ubuntu"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Leed on 2006-12-02
Hi 

I'm trying to do some network administration in Ubuntu, I'm here in a home lan, 5 PCs, 3 laptops, 2 printservers, 2 access points, 1 router, 1 dsl-modem, 1 network-disk. 

What I'm looking for is a tool that can match the windows freeware program "Network Scanner" by SoftPerfect
[http://www.softperfect.com/products/networkscanner/]("http://www.softperfect.com/products/networkscanner/")

What it does is send a ping to every ip in the same Network, upon answer identify the device and if it has windows shares... these are displayed and can be accessed by clicking on the device. This is far more effective than the windows/nautilus network browsing and also shows the devices these do not list. I just can't find anything like this for ubuntu. 

Can anyone give me a good tip?
Dave

---

### Post by tribaal on 2006-12-02
Would be quite handy, I agree.

Might not be that hard to code actually... Just a thought. Anyways, unfortunately I don't know if anything equivalent exists for Ubuntu... :(

- trib'

---

### Post by sardion on 2006-12-03
nmapfe

the interface is somewhat confusing, so read the man pages:

man nmap
man nmapfe

if you get stuck.

nmapfe can do all of what you want and more.  i use it for that exact purpose on several networks.

---

### Post by Leed on 2006-12-03
Hey that's pretty nice, as you say the interface does take a little getting use to, but it is handy. 

Thanks a lot sardion :D

---

### Post by xeo_pt on 2006-12-03
Thanks a lot for the info, I was alsoo looking for a tool to help
manage my network.

Regrads.

---

