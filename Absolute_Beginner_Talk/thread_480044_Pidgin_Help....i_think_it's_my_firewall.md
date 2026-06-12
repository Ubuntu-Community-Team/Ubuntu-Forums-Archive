---
title: "Pidgin Help....i think it's my firewall"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by icaughtfire818 on 2007-06-21
I've just downloaded and installed Pidign and it won't connect.

The software runs correctly, but I can't get it to do more than tell me it's trying to connect. I've messed with the proxy settings, and the servers, but nothing seems to work.

It could be my firewall...*shruggery*

Any ideas or does anyone know what's going on?

---

### Post by pkarjala on 2007-06-21
Have you tried temporarily disabiling your firewall to see if it is indeed the culprit?

---

### Post by icaughtfire818 on 2007-06-21
I'd love to, but I'm not 100% sure if I've even got a firewall up.

I never set one up...

So if it's not my firewall, what could it be?

---

### Post by skymera on 2007-06-21
are you on a router?

---

### Post by icaughtfire818 on 2007-06-21
Yeah! That sounds about right.....

[I'll be the first to admit that I'm a total idiot when it comes to most computer things, btw]

Why?

---

### Post by skymera on 2007-06-21
so your on a router?

maybe its blocking the port Pidgin uses..

---

### Post by icaughtfire818 on 2007-06-21
So if it's blocking the port that Pidgin uses, could I just put Pidgin on a different port? (I'm not sure how to modify my router...hmm....)

And if I could, which port would that be?

Oh btw, I'm using Piding for AIM(which uses port 5190), MSN(port 1863) and Yahoo(pager port 5050 and file transfer port 80) protocol. Can I have them all use the same port?

---

### Post by pkarjala on 2007-06-21
It's generally not a good idea to have programs running off of the same port.  What you may want to do is find out the specific brand of router you have, and figure out how to add Port Forwards in that router.  If you do know the brand and model number, go ahead and post it here--we might be able to find you a handy walkthrough.

---

### Post by icaughtfire818 on 2007-06-27
> **pkarjala said:**
> It's generally not a good idea to have programs running off of the same port.  What you may want to do is find out the specific brand of router you have, and figure out how to add Port Forwards in that router.  If you do know the brand and model number, go ahead and post it here--we might be able to find you a handy walkthrough.

My router is an Actiontec and the model number is RI408.

:)

---

### Post by mendingo84 on 2007-06-27
Hey, i'm having the same problem...but i'm using Gaim (older for Pidgin). I changed the port for Yahoo from 5050 to 80 and it works now...somehow! But it took an infinity to login!

---

### Post by astanix on 2007-06-27
Im thinking yahoo changed something yesterday or the day before because I haven't been able to login for a while.  My msn, aim, and icq all work still.

---

### Post by icaughtfire818 on 2007-06-29
> **mendingo84 said:**
> Hey, i'm having the same problem...but i'm using Gaim (older for Pidgin). I changed the port for Yahoo from 5050 to 80 and it works now...somehow! But it took an infinity to login!


I tried this and it is taking an infinity to login. Any tips for AIM and MSN, specifically?

---

### Post by Hasen_A on 2007-10-12
I've had the following problem. I am sitting in a univerity dorm where everything worked perfectly. Then they shut down the wireless LAN and when it was set up again, a lot of stuff no longer works: mail uploading smtp, and MSN messanger can no longer connect.

I haven't changed anything in the settings and believe that the ports are closed. I've checked them with the console and on several internet sites. Now the question is whether i can redirect gaim to use another port for MSN instead of port 1863, since that worked for the icq port, which i changed to 443. Is there a specific port which i need to use and how can I find out which ports are available meaning they arent blocked by my ISP?

THanks beforehand.
andy

---

### Post by Candace on 2007-11-20
I know this post is old, but I am also having the same problem trying to connect to msn through pidgin on my university's wireless. I have tried the suggested ports (50, 443, aim: 5190) and none of them work. The default is 8163 which doesn't work. Can you please give me a pointer for what I need to do to get Pidgin/msn working at school? (btw, aim works fine but I only have one buddy on aim, so I want to be on msn). 

Thanks.

---

### Post by philinux on 2007-11-20
Try Kopete. I've not touched iptables or have a firewall, nor touched the router and it just works.

By the way it's a wired router.

---

### Post by Hasen_A on 2007-11-20
> **Candace said:**
> Can you please give me a pointer for what I need to do to get Pidgin/msn working at school? (btw, aim works fine but I only have one buddy on aim, so I want to be on msn). 


Creating a ssh tunnel worked for me using the following code
```
ssh -D 127.0.0.1:1080 username@ssh-server-address
```
Now just use socks4 settings in Pidgin with server 127.0.0.1 and port 1080. All other settings for MSN should be reset to the default values. It works for me.

---

