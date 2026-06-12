---
title: "Router changed out, now wireless kaput"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-04-19
Well, here I am again! My son decided he wanted to change out the wireless router. Supposedly the settings are the same, but now it won't even recognize my laptop as sending a signal. I cannot ping the router. I don't want to plug in the lan, or it will bump all the wireless settings. 

I'm looking in the router settings, and nothing seems amiss. He says it has to be something in my ubuntu laptop not working... Do linux settings just change themselves at times? I haven't changed anything in the box at all...

This isn't what I had hoped to spend my evening on... fixing something I didn't break... Oh JOY!](*,)

iwconfig shows I am able to get the router's signal, but I do not get an 'access point' or a mac addy

---

### Post by Papa-san on 2006-04-19
Is the MAC address the 'serial' found under sudo lshw -C network under my wireless card?

---

### Post by 5-HT on 2006-04-19
[quote=Papa-san]Is the MAC address the 'serial' found under sudo lshw -C network under my wireless card?[/quote]

Yup (sorry can't help with anything else).

---

### Post by Papa-san on 2006-04-19
[QUOTE=5-HT]Yup (sorry can't help with anything else).[/QUOTE]
Thanks!
That was at least a little moral help... As soon as I put that in it blew his settings out. Still doesn't get me online, tho'

I figured that with the linux box I am OK in the DMZ. Is this OK, or not?

---

### Post by Papa-san on 2006-04-19
I broke down and plugged in the Cat-5. I tried to ping the router, and it says it isn't allowed.
 I'll search the router model to see if there are answers elsewhere...

---

### Post by 5-HT on 2006-04-19
[quote=Papa-san]Thanks!
That was at least a little moral help... As soon as I put that in it blew his settings out. Still doesn't get me online, tho'


I figured that with the linux box I am OK in the DMZ. Is this OK, or not?[/quote] 
I don't use wireless myself so I wouldn't be of much help in that respect.
However, if inputting your NICs MAC into the router's configuration made the other computer loose connection, what about doing a goold ol' powercycle (it's a long shot, but if everything else is configured properly for the router and computers, it may be worth a try)?

Easiest way to get it done fully would be to:
1. Shutdown any computers on the network
2. Unplug power to the modem and router
3. After about 15 seconds, plug the modem back in
4. Wait until the modem gets block sync
5. Plug the router back in
6. Give it a good 20 seconds and boot the computers back up


About having your box in the DMZ, if it works only in the DMZ you'll loose the firewall capabilities of the router, but you'll get a connection.
Depends on your preferences and security concerns.
Ideally it would be best to not have it in the DMZ unless you need it there for some reason.
One thing to note though is that Ubuntu does not have any world-listening services turned on by default.

Hope you get it working.

---

### Post by Papa-san on 2006-04-19
Hmmmm. I no longer have a linksys router. It is now a D-link... Evidently this makes a difference.
 Any help here..?

---

