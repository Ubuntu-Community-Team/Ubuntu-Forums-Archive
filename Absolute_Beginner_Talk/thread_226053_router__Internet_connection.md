---
title: "router / Internet connection"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Xios on 2006-07-30
hello there, im compleatly new to ubuntu, i have tried Knoppix before so i have a very small limited ammount of experainace with linux but not enough.

this is my problem

i have this router

[http://www.ebuyer.com/UK/product/90975/rb/20727716720](http://www.ebuyer.com/UK/product/90975/rb/20727716720)


Its a nice router its hooked up to all my windows XP computers, and works fine.

once on ubuntu, i can connect to the router (via wired) and i can change settings as if i were using it on windows, however when i try to connect to any website routing through the router, it does not load, or when it does firefox gives me an error and tells me to check my network settings

please help, im desperate to get off of windows and onto linux, but i cant survive without the internet...lol

(also compleatly unrelated, is there a way i can use MSNMessneger on ubuntu, as all my friends have it and i have no choice...lol)

Please reply asap,

---

### Post by meney on 2006-07-30
If you go System>Administration>Networking see if your connection is active & its set to DHPC. If this is all set up fine, I would think it might be a setting in your router.

As for MSN :) if you go Applications>Internet>Gaim. This is the messenger that comes with Ubuntu and supports MSN, ICQ, AOL etc.

---

### Post by Xios on 2006-07-30
Thank you, however its set as DHCP and it is active, 
the settings cannot be wrong on the router as every other machine in the building connect to the internet fine.

do youo think that ubuntu isnt reading my router proberly, say i have not installed it proberly, or it has become corrupted, other settings not right or somthing

this is really important to me at the moment so help as soon as possible would be of great appreciation  :-D

---

### Post by Bdubbya on 2006-07-30
sounds like you're not useing the correct device(eth0, eth1) as the gateway.

If you know anything about IP subnetting this will make more sence.
if intrested, [http://www.learntosubnet.com/](http://www.learntosubnet.com/)

Disclaimer: This solution is given with out any real Linux experance. it's purley from a TCP/IP stand point.

---

### Post by Xios on 2006-08-01
I have descovered the problem, it had nothing to do with the networking connection between the computer to the router, the router forces IPv2, and is not downgradeable, so instead i turned it on in the settings used by firefox.

Works fine now.
Thank you for trying to help anyway

---

### Post by sportsblue on 2006-08-14
Xios - do you remember what you did to fix this?  I am a newbie to Ubuntu and have spent the last week trying to connect with the same router (wired connection) as you but can't.

I've checked the network connections and they appear to be correct.

How did you turn on IPv2?

I have an added complication of a second pc on windows also wired into the router (which connects fine).

Can you (or anyone else) help?

---

### Post by sportsblue on 2006-08-14
A little trigger happy with my previous post - I've found out how to fix the mozilla connection with this router.

Open Firefox and type about:config in the address bar
scroll down to network.dns.disableIPv6 
double click it so that it changes from false to true 

Now try entering an address - hopefully it will load.

I found this posted (at Tue 18th July 2006 11:52:am) in the reviews of the safecom router linked in the first post on Ebuyer.

I am much happier now... :D

---

