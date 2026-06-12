---
title: "Bizzare internet problem"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by THE_DEATH_M on 2007-10-03
I've been fighting the ubuntu problems of my box for some time, but never faced anything like this, so I'll try to explain.
First of all, I'm currently using Kubuntu 7.10 beta (note that the problem appeared when I was still on 7.04). Some time ago, my international net became horrible, i had to try about ten times until a page is displaied, always saying that there is no connection to the server. On the other hand, I also noticed that there is no such problem with servers in my country. So, I tried "mtr www.any_international_server.com" a few times, to see where things screw up, and in all cases mtr reported that one same hop makes losses of about 40% of the packages (a gate that my ISP uses for international connections). So I was just ready to call the ISP for an explanation, when I decided, just to make sure, to do the same test with my XP (on the other partition). And the winmtr I used reported about 30% package loss at the same hop. BUT when i tried to use the browser (opera, but I guess it doesn't matter), there was just no problem, any page would open with nearly no delay. And here I am at the zero again :(
Any idea what could that be?
ADD: after the dist-upgrade, I also sometimes need to reload the network interface after boot to make any internet connection possible.

---

### Post by p.i.m.p on 2007-10-03
did you try to disable ipv6? for firefox, go to about:config and change the value of network.dns.disableIPv6 to true

---

### Post by THE_DEATH_M on 2007-10-04
thanks a lot, seems to work... (for now :D)

---

