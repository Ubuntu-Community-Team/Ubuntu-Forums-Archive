---
title: "No internet connection even though cable modem is plugged in"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Losgann Mor on 2008-03-04
Hello -- I am brand new to Linux. I've just built a new system, and I installed Ubuntu 7.10 on it today. Installation went swimmingly, no error messages or anything. We have DSL, I've connected the ethernet cable from the DSL modem to LAN port on the computer, and the Network Manager icon in the upper right  shows an enabled, connected wired network connection, yet Firefox will not open any web pages, and I cannot connect to any repositories in Synaptic. Can anyone help me figure out what the problem could be or where I need to go/what I need to do to fix it?

---

### Post by glennric on 2008-03-04
From a terminal try 
```
ping www.google.com
```
and see if that gets anywhere.

---

### Post by Moop on 2008-03-04
You may need to reboot your modem. Just unplug it for a minute or so and then plug it back in and see if you get a connection.

---

### Post by strawberryjam on 2008-03-04
Go to a terminal and type

sudo pppoeconf

it will take you through a wizard like interface to set up your connection , also how to turn it on or off.

hope it helps

---

### Post by Losgann Mor on 2008-03-05
Attempts at pinging get me the same error message every time:
> 
ping: unknown host [www.google.com](www.google.com)

I tried several other websites and got the same response.

I tried switching the modem off and on, also unplugging it and plugging it in again, but neither made any difference.

I tried pppoeconf twice, and got the following message both times:
> 
Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure  may also be another running pppoe process which controls the modem.


I should perhaps mention that I am using the same modem and cable that I am currently using to access the internet and posting to the forum, so I know the modem & cable are good, because they work just fine when I connect them into this computer. It's just the new one that doesn't work.

---

### Post by AvalonSkies on 2008-03-05
[COLOR="Silver"]If you unplugged your modem from a router or a switch before plugging it directly into your computer, it could be that you're using a crossover network cable instead of a straight-through. Without any idea of your setup or anything, that's my first guess. I don't know what that kind of problem would look like in Linux, though-- so like I said: it's a first guess.

**The Short Version:** Try a different network cable, if you have one. :)[/COLOR]

**EDIT:** Woops. I didn't see the two sentences at the very bottom of your last post. My bad.

---

### Post by deadmnky on 2008-03-05
did you try turning your computer off while the modem was resetting?
i had a similar issue with my desktop and for some reason resetting the modem while the computer was off helped. wait like a minute or so when you do it

---

### Post by Losgann Mor on 2008-03-06
Huh... after a couple of days of not working, it suddenly worked out of the blue. Go figure. Thanks for the suggestions, guys. 

(Of course, once one problem is solved, another one rears its ugly head, but that's a different thread. :))

---

### Post by Kadin2048 on 2008-03-06
Glad that you got it working.  I was going to suggest as a next step, that you try spoofing the MAC address of the working machine onto the Ubuntu one, just in case your ISP is doing something shady with locking based on MAC addresses.  That's not too common but it's not unheard of either. It's something more common on cable modems than DSL, though (or at least that's been my experience).

They may go through every few days and reset or purge their tables so that might explain why it suddenly started working.

---

### Post by deadmnky on 2008-03-06
glad it is working thats what happened to mine as well i tied and tired then it just started working later that night.

---

