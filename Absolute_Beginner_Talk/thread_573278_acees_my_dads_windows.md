---
title: "acees my dads windows"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-11
if i plug in my dads Windows XP laptop via ethernet into my machine.

how do i access his fdiles?

---

### Post by Depressed Man on 2007-10-11
He'd have to share (or you have to setup) some share folders on his Windows laptop. Should be as easy as right clicking then click share this folder or properties then sharing.

Setup a username/pw and then make sure the firewall will allow connections from whatever hostname or IP you are using. Then you have to map it as a network share by clicking places > connect to server > service type (dropdown menu to windows share). Server would be the hostname of the Windows laptop or its IP. Share would be the folder you shared. For example my windows desktop (and well Linux as well)'s share folder is called LAPTOP_SHARE.

So I would put in for server 192.168.1.100 with the share being LAPTOP_SHARE

---

### Post by Dr Small on 2007-10-11
If he has sharing enabled, and you have samba installed, you should be able to type this in the address bar of Nautilus:
```
smb://*ipaddress*
```

---

### Post by dca on 2007-10-11
Wait a minute you're connecting the ethernet cable from his laptop into your PC?  Or through a router...  If it's plugged peer to peer you would need a crossover ethernet cable...

---

### Post by rahimveron on 2007-10-11
I have ethernet cable that i use to connect my ADSL modem with my computer. Can i use this ethernet cablle to connect peer to peer as said above?
Is crossover ethernet cable  different from this ethernet cable that i have?

---

### Post by phr0ze on 2007-10-11
A cross-over cable is wired differently. It's needed if you want two hosts to talk directly. You should be able to get one fairly cheap. The other option is to get a 4 port router for your home, then at least you will have some protection with NAT.

---

### Post by tech9 on 2007-10-11
> **skymera said:**
> if i plug in my dads Windows XP laptop via ethernet into my machine.

how do i access his fdiles?

make sure you use a crossover cable if you are going to hook up to the latop directly.

---

### Post by dca on 2007-10-11
Crossover allows for the communication both ways simultaneously...
 
[http://compnetworking.about.com/od/networkcables/g/bldef_crossover.htm](http://compnetworking.about.com/od/networkcables/g/bldef_crossover.htm)

---

### Post by brennydoogles on 2007-10-11
> **rahimveron said:**
> I have ethernet cable that i use to connect my ADSL modem with my computer. Can i use this ethernet cablle to connect peer to peer as said above?
Is crossover ethernet cable  different from this ethernet cable that i have?

You will either need a router or a crossover cable. You can buy crossover cable at any electronics store, or if you have spare ethernet cable and are good at this kind of thing just reverse all the leads on one side and that will make a crossover cable.

---

### Post by rahimveron on 2007-10-12
> **brennydoogles said:**
> You will either need a router or a crossover cable. You can buy crossover cable at any electronics store, or if you have spare ethernet cable and are good at this kind of thing just reverse all the leads on one side and that will make a crossover cable.

Thats a scary thought. I will buy a crossover cable ,rather.

---

### Post by tech9 on 2007-10-12
> **rahimveron said:**
> Thats a scary thought. I will buy a crossover cable ,rather.

Making crossover cables is actually very easy...
Just remember one end is...

568A Standard...

whitegreen, green, whiteorange, blue, whiteblue, orange, whitebrown, brown


and the other end is...

568A Standard...

whiteorange, orange, whitegreen, blue, whiteblue, green,  whitebrown, brown

And really the only difference is switching the two pairs whitegreen, green and whiteorange, orange around.

These are the only two twisted pair that you need to make a cross-over cable

Piece of Cake\\:D/

---

### Post by rahimveron on 2007-10-14
Thanks tech9 for the info.
Another query, can i use the same ethernet cable that i have modifies for my ADSL modem?

---

