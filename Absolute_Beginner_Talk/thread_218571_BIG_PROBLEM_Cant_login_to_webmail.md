---
title: "BIG PROBLEM Cant login to webmail"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by tfm1 on 2006-07-18
Please help me. Im quite new to ubuntu i have the latest release i have fast wireless internet that works and i use both mozilla firefox and opera web browser but I cant login to email such as hotmail, yahoo and gmail!!!! And it is very embarrising to show my friends such a beautiful operating system that doesnt open hotmail.

I dont have firestarter. I have played around with the tls and ssl stuff. But it still says connection timeout when i click on login. 

This also happens on secure sites such as skype.

What is wrong!!

At least reply if u have a similar problem, just so that i dont feel lonely.

Ok if the problem is that i have to be super user to open secure sites as i had to, to open encrypted dvds, how to i make a launcher to make sure that every time i open mozilla firefox or opera that it is opened as super user or how can i change my user account to be super user?

I havent tested the sudo on mozilla, i have to wait like a month as im abroad.

---

### Post by Kurt` on 2006-07-18
Not sure if this is directly related to your problem, but if you haven't done it yet, please do:

Visit the page 'about:config' in Firefox.

Scroll down to network.dns.disableIPv6

Set it to TRUE.

Restart Firefox.

That should fix any problems with sites timing out or loading insanely slow.

---

### Post by T700 on 2006-07-18
> **tfm1 said:**
> Ok if the problem is that i have to be super user to open secure sites as i had to, to open encrypted dvds, how to i make a launcher to make sure that every time i open mozilla firefox or opera that it is opened as super user or how can i change my user account to be super user?

I havent tested the sudo on mozilla, i have to wait like a month as im abroad.

This doesn't make sense.  You don't need to log in as root or invoke a web browser as root to visit a secure site.  Are you sure you didn't tinker around with some of the settings in your browser?  Have you tried installing/using a different browser and seeing if that one works?

Paul

---

### Post by Unconscious on 2006-09-25
I too have this problem. I cannot use yahoo webmail for over a month. I've tried all the various suggestions for speeding up firefox (disable IPV6, etc.) Here's what I've determined thus far:
[LIST]
[*]It's not the browser. Same thing with epiphany
[*]It's not the network, or the router. My XP box w/firefox, works just fine.
[*]I don't think it's Ubuntu. It works just fine from my Ubuntu box at work.
[/LIST]

So... What can I do? I really dislike having to use windows for anything. I need to have a M$ box for VPN access into my employer's network. However, I'd prefer not to use it for my own e-mail.

The friendly folks at yahoo and sbc blame it on Ubuntu, and snidely refuse to address my issue on the basis that "open source software cannot be expected to function as reliably as professionally developed commercial software".

I suspect that it may have something to do with certificates, but I don't know how to find out. Can anybody offer me at least a direction in which to investigate?

---

### Post by stilus on 2006-09-25
I am quite sure it's something to do with wireless + encryption, but sadly cannot offer any help.  Since I was not able to fix this (and my usb-wireless dongle kept giving my computer kernelpanics and me headaches), I decided against using it for now... 
as for yahoo snubbing at opensource (like Unconscious reported): 
[http://searchdns.netcraft.com/?host=yahoo.com&position=limited](http://searchdns.netcraft.com/?host=yahoo.com&position=limited)

FreeBSD was opensource, last time I checked :rolleyes:

---

### Post by D10 on 2006-09-25
But using an open source OS in a server/backend enviroment is different than supporting an open source desktop, and/or FOSS (free open source software).

---

### Post by grayhorse on 2006-10-01
I've noticed this problem also - I've done the IPv6 trick, and firefix loads a bit quicker, but still doesn't reach Gmail. Most annoying. 

Konqueror can reach Gmail, however. There may be something subtle going on here, but I agree there should be a solution, as it appeared quite recently out of the blue.

About the same time evolution decided to segfault on my machine, too, I'm afraid :(

---

