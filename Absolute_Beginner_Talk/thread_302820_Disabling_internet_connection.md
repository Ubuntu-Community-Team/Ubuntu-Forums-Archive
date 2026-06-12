---
title: "Disabling internet connection"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2006-11-19
Good Morning,

I have a real concern about leaving my internet connection on at all times while I am working on other things.

I have an ethernet card and a DSL modem and am using dapper as my distro. I looked at the forums, read working with your desktop, and yesterday purchased the offical Ubuntu book all to no avail.

I tried using through a terminal the commands:

sudo poff dsl-provider

but when I test it with firefox or opera the connection is still there.

Thank You,
Carolyn

---

### Post by xpod on 2006-11-19
lol....I`ve seen plenty folks toiling to get an internet connection on....

But never "off":D 

Cant you just deactivate it in "networking"??

---

### Post by b_martinez on 2006-11-19
try 

sudo ifdown eth0

hth
Bill

---

### Post by Carolyn62 on 2006-11-19
> lol....I`ve seen plenty folks toiling to get an internet connection on....

But never "off"

Cant you just deactivate it in "networking"??

What can I say? Up 'till now I was (emphisis on was) a diehard windows user.

I have considered doing that but that would only be accessible in the root account...right?

> try

sudo ifdown eth0

Okay, but before I try it I have to ask a dumb question....How do I get back on? Is it by using:

sudo ifup eth0

I am not trying to be funny, I am that new.

Thank You,
Carolyn

---

### Post by xpod on 2006-11-19
> What can I say? Up 'till now I was (emphisis on was) a diehard windows user.

lol....I wasn`t and have only used this the same few months i used windows but i still could`nt tell you anything much,other than deactivating it in networking.

I would just pull the wire out if i was that bothered:D 

I`ve got an always on connection thats.....always on.I`ne never learned how to turn it off either so dont worry about it...:D 

Good luck though

---

### Post by hal10000 on 2006-11-19
@Carolyn62:

do a [COLOR="Red"]sudo /etc/init.d/networking start[/COLOR].
or ifup eth0

That's all.

But, usually its not necessary to cut off your connection, because we are not in the windows world here.

---

