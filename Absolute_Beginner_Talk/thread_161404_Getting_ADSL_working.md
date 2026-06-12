---
title: "Getting ADSL working"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by shmida on 2006-04-17
Im very new to ubuntu and im finding it hard to get internet working on ubuntu
works fine on XP please help


Thanks

---

### Post by drowner on 2006-04-17
I just had this problem! and i fixed it!

Be more specific...

---

### Post by shmida on 2006-04-17
> Be more specific...
I've configured the modem and all and it works fine XP
but when on ubuntu the internet just doesnt work

---

### Post by drowner on 2006-04-17
:D

Specific... lets start with..

1. What sort of modem? Whats it plugged into?

(PS dont say 'A good one, the back of my pc!'

---

### Post by shmida on 2006-04-17
[QUOTE=drowner]:D

Specific... lets start with..

1. What sort of modem? Whats it plugged into?

(PS dont say 'A good one, the back of my pc!'[/QUOTE]


Dlink DSL 504T, tis ethernet modem and everything is plugged into right place

---

### Post by drowner on 2006-04-17
Under the networking settings of Ubuntu (im also a n00b, and i cant remember exactly where it is!) there is a eth0 options.... which by default is deactivated if you didnt have your router up and running when you installed ubuntu. THat was my error LOL

Try and click the activate button ;)

PS If i wasnt on a windows box at work, id tell you exactly where it was. Someone help?

---

### Post by jorn on 2006-04-17
System > Administation > Network

---

### Post by slimdog360 on 2006-04-17
I only recently, a few days a ago, installed unbuntu myself and the adsl was not working. What I found is that when it was installing something went wrong when it was trying to configure it there so  just thought id leave it and fix it later. Couldnt do it, so I reinstalled it and this time I found the problem.
    I cant remember the exact details but I had to choose some DHCP (or whatever its called) with a name or something similar. Basically i chose that option and I had to put in an ip adress, 192.168.1.1, so it was the ip of the router or my computer im not sure. From there it worked beautifully.
Sorry I cant remember the exact details but I tried to help anyway.

---

### Post by wat3r on 2006-04-17
Do you have a router, or just a modem?

---

### Post by shmida on 2006-04-17
> Do you have a router, or just a modem?
Router

---

### Post by wat3r on 2006-04-17
Ok. I had a problem connecting my ADSL, but I did not have a router, so I tought I could help you, if you did not have a router. But since you have, I can't help you. Sorry.

---

### Post by drowner on 2006-04-17
Try what i said.

---

### Post by shmida on 2006-04-18
i tried to do sudo pppoeconf in terminal and ran the test but it the test didnt go smoothly it had an error or something.
could this be the problem

---

### Post by majstor on 2006-04-18
[QUOTE=shmida]i tried to do sudo pppoeconf in terminal and ran the test but it the test didnt go smoothly it had an error or something.
could this be the problem[/QUOTE]

If you have a router you only need to have your network (lan) activated. Try what drowner said

---

### Post by carverj on 2006-04-18
try configuring the network settings as per previous posts, restart the computer
(or being linux maybe not required) and send a message to your router to see if it can hear your computer by opening command prompt (Applications> Accessories > Terminal) and typing ping 192.168.0.1

---

