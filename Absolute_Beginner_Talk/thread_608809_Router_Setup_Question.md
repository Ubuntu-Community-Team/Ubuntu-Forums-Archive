---
title: "Router Setup Question"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by davebridges on 2007-11-10
sorry if this is already in other forums, but i couldnt find it.  I have at&t dsl, which was setup before moving from xp to ubuntu.  I connect motorola modem->netgear router->ubuntu 7.10 computer.  If i go modem->computer it works all fine and dandy, but when i try to go through the router, no dice.  The router setup wizard will not set up the router (I am sure the username and password are ok).  

ATT tech support dosent support Linux (there's a cause for someone to make some noise about), so won't give me a hand.  He mumbled something offhand about setting up a modem bridge, but then told me the best way would be to reinstall windows and he could set it up then.  I bet this is some easy solution for you linux wizards.  Thanks eh!

---

### Post by deep.tinker77 on 2007-11-10
Did you have this setup working before using linux? Have you checked to make sure your dsl modem and router aren't conflicting with each other (i.e. both have I.P.'s of x.x.1.1)? I did that along time ago and had to change the 3rd octet on my router so it ended up being x.x.2.1 on my router and x.x.1.1 on my modem. Hope it helps. Good luck.

---

### Post by Duck2006 on 2007-11-10
Can you get into the router through your firefox?

ie open firefox and in the adderss bar type the IP adderss 198.xxx.xxx.xxx
with the router connected.

---

### Post by davebridges on 2007-11-10
yup, my router is at 192.168.1.1, so if i go there i can connect to the router.  if i do that without the router connected, it goes to the modem (motorola) setup page.  The problem is when setting up the router, it dosent seem to take

---

### Post by deep.tinker77 on 2007-11-10
> **davebridges said:**
> yup, my router is at 192.168.1.1, so if i go there i can connect to the router.  if i do that without the router connected, it goes to the modem (motorola) setup page.  The problem is when setting up the router, it dosent seem to take

Ok, i think your problem is that they are both fighting for the same IP. Give your router the IP of 192.168.2.1 and see if that clears it up.

---

### Post by Witling on 2007-11-10
Let's go back to that thrilling question by Deep.Tinker77: Did this setup every work? In other words, did you have it working in Windows. For what it's worth, my cable modem and router have different third octets.

---

### Post by deep.tinker77 on 2007-11-10
> **Witling said:**
> Let's go back to that thrilling question by Deep.Tinker77: Did this setup every work? In other words, did you have it working in Windows. For what it's worth, my cable modem and router have different third octets.

Mine as well. When he said that they hooked up the modem and went to 192.168.1.1 for both the modem and router I thought that had to be the problem.

---

### Post by davebridges on 2007-11-10
ok... sorry for the newbiness, but how to i manually set the router and computer to specific ip's

---

### Post by deep.tinker77 on 2007-11-10
No problem, we all started out somewhere :) You dont really have to set your cpu to a specific ip address, dhcp will work fine. To set your router's ip, you can probably use the set-up wizard that will probably be one of the first options you have once you log in to your router. If you post your router's model, i can help you find the instructions if you aren't able to do it thru the router set-up wizard. They are usually pretty straight foward. 

You will probably have to disconnect your modem from your router due to the fact that they both still have the same IP....unless you want to change your modem's ip, but lets stick with the router for now.

---

### Post by Witling on 2007-11-10
Routers and cable modems are typically accessed using a browser. Enter the IP address of the device. It will look something like

[http://192.xxx.xxx.xxx/](http://192.xxx.xxx.xxx/)

---

### Post by davebridges on 2007-11-10
its up and running now (i had to set it to bridge connection on the modem setup, then restart).  thanks for all the help guys

---

