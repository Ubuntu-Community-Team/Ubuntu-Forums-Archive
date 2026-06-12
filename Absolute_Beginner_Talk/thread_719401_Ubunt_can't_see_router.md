---
title: "Ubunt can't see router"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Cadbury_Gal on 2008-03-09
Hi, 

I really hope someone can help me out.  I have install ubuntu 7.10 on to my pc.  Everything is fine apart from I cannot get an internet connection.  Which obviously means I cannot update it or anything.  

The internet connection is wired, and was working perfectly ok when windows XP was installed on there.

Would be grateful if someone could shed some light on this please.  I am a complete newbie when it comes to ubuntu, so please dont confuse me!!!

Hope someone can help out!!!

Cadbury_Gal

---

### Post by pommattski on 2008-03-09
Hi,
So that someone can help you, you need to provide a little more information about how you are trying to connect to the internet:
Do you have an external or internal modem or router?... What type is it?.... 
Is it connected to your computer by Network cable or by USB cable?

---

### Post by Cadbury_Gal on 2008-03-09
Hi, 

The router is a netgear, and it is connected to the PC using a cable.

I'm running Ubuntu 7.10 on an intel PC.

---

### Post by seventhc on 2008-03-09
Do you have the router set up for DHCP? or have you hard coded it.
Also it seems you have 2 computers hooked up, make sure the link light is on. Should have a light for each connection:example I have a netgear that allows 4 computers to be connected by wire, so for every computer connected there is a light that is lit.
Do you know how to get into your router?? 192.168.1.1 maybe?
you should see if you can ping it, but verify the address from your windows machine since that one is working.
Open the command prompt and type in
```
ipconfig
```the gateway will be the info you want. Then go to ubuntu open a terminal and type in
```
ping 192.168.1.1
or whatever the gateway was
```post back results.

---

### Post by ByteJuggler on 2008-03-09
Please, open a terminal (Applications->Accessories->Terminal).  Then copy and paste the following command into the terminal:

```
ping -c 3 64.233.183.147
```

Please copy the output and post it back here.  

Then run the following command: 

```
ping -c 3 www.google.com
```

Again please copy the output and post it back here.

The 2 commands are equivalent, but the second one will involve name resolution.  Comparing the output will help me diagnose the problem.  I have a suspicion this may be an issue with your router and IPv6 DNS resolution, for which a workaround exists in the glibc6 library for Ubuntu 7.10, but which unfortunately wasn't included on the original release/install CD.  If this proves to be the case, I'll post you instructions for updating this library, after which your problems should disappear.

---

### Post by Cadbury_Gal on 2008-03-09
Thank you for all your help and advice, but have decided to put windows XP back on. 

I will pop back on the forum now again , as I have installed 7.10 on another hard drive on a different PC, so if I have any probs I will be back,

Thanks again

Cadbury_Gal

---

