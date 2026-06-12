---
title: "Cannot load any pages on Firefox"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by bandeiram on 2007-05-14
Hey there everyone... I'm like a newborn when it comes to the Linux OS... I'm using Ubuntu 6.06 Dapper Drake, and up until last night I was able to get perfect connectivity to the internet and load every page I usually want... However, this morning I found that I have lost my connectivity capabilities and am not able to get it back... Could someone please help me....

Once, I go into the terminal, I run the following code:

[COLOR="Red"]pon dsl-provider[/COLOR]
I get... [COLOR="Blue"]Plugin rp-pppoe.so loaded[/COLOR]

After a few seconds, I entered [COLOR="Red"]plog[/COLOR]
I then got... 
[COLOR="Blue"]replacing old default route to eth0 [10.1.1.1][/COLOR]
[COLOR="Blue"]Cannot determine ethernet address for proxy ARP[/COLOR]
[COLOR="Blue"]local IP address XXX.X.XX.XX[/COLOR]
[COLOR="Blue"]remote IP address XXX.XXX.XX.XX[/COLOR]
[COLOR="Blue"]primary DNS address XXX.XXX.X.XX[/COLOR]
[COLOR="Blue"]secondary DNS address XXX.XXX.X.XXX[/COLOR]
[COLOR="Blue"]Plugin rp-pppoe.so loaded[/COLOR]
[COLOR="Blue"]pppd 2.4.4b1 started by bandeiram, uid 1000[/COLOR]
[COLOR="Blue"]Timeout waiting for PADO packets[/COLOR]
[COLOR="Blue"]Unable to complete PPPoE Discovery[/COLOR]
[COLOR="Blue"]Exit.[/COLOR]

Then I typed into the terminal [COLOR="Red"]sudo pppoeconf[/COLOR]
I then got the blue screen, which said:

[COLOR="Red"]I found 1 ethernet device:
eth0[/COLOR]
I chose [COLOR="Blue"]YES[/COLOR]
It looked for a connection and at both instances the message displayed was:
[COLOR="Blue"]TIMEOUT WAITING FOR PADO PACKETS[/COLOR]

What can I do to fix this problem?!?!

I hope to hear from someone soon...

Thanks in advance,

bandeiram

---

### Post by oilchangeguy on 2007-05-14
are you sure there's not a problem with your isp? have you looked at your modem? are all of the lights on as normal?

---

### Post by bandeiram on 2007-05-14
I'm not sure what ISP means, however, I'm able to connect to my other computer (which is the one I'm writing on right now), and not with the ubuntu 6.06 one...

bandeiram

---

### Post by oilchangeguy on 2007-05-14
> **bandeiram said:**
> I'm not sure what ISP means, however, I'm able to connect to my other computer (which is the one I'm writing on right now), and not with the ubuntu 6.06 one...

bandeiram
isp=internet service provider
do you use a router? or a single modem, and switch computers?

---

### Post by bandeiram on 2007-05-14
> **oilchangeguy said:**
> isp=internet service provider
do you use a router? or a single modem, and switch computers?

Thank you and sorry for my ignorance...

I use a single modem and switch computers... It's just odd, cause sometimes, it seems to work perfectly well, and other times it gives me this problem...

bandeiram

---

### Post by rillip on 2007-05-14
It looks like you're not getting an IP address from your ISP.  Could be a local networking/configuration issue or could be an issue with their DHCP server.  Do you have the ability to set a static IP?  If you don't know, you don't.  ISP's usually charge quite a bit for that.

Also, I'll be frank in saying I don't recognize the commands you're running. But you state you're new to Linux. These seem rather at odds.  If you can describe more of where you got these commands or what you were trying to acomplish when the issue arose, it might provide some needed information.

I really don't know how to resolve your issue, don't have DSL or any experience with it.  Do you have another OS on the system to ensure the DSL isn't the issue?

Edit: you might also think of posting this in the networking section, you might be able to get some more specific help there.

---

### Post by oilchangeguy on 2007-05-14
what you'll need to do is, either turn off (unplug) the modem each time you switch computers. or get a router. that way the ip address will be assigned to the router, and you won't have to reset it each time.

---

### Post by bandeiram on 2007-05-15
Hey there!!! Thank you for everyone's understanding on the matter...

Rillip -- I am new to the Linux OS (Ubuntu 6.06 DD). I'm only running the standard commands... <plog> <pon dsl-provider> <poff dsl-provider>... those are in red...

the ones in blue are the messages I'm getting...

Still don't know what to do... I can connect to this PC, but not the other...

Cheers

bandeiram

---

### Post by bandeiram on 2007-05-15
Still not able to load any pages, no matter what kind of effort I put into trying to solve the problem... The internet works fine in one computer (with a Windows OS) however once I try to make it work on my Linux OS (on another computer) it complains like mad...

Every now and then it seems to work fine, however, it has a mind of its own, as I don't get to decide when it works or why...

Like I previously said, I put in a couple of commands on the Terminal

pon dsl-provider (to connect)
plog (to check the connection)

then I get the message

Timeout waiting for PADO packets
Unable to complete PPPoE Discovery

Well, I hope someone can help me with it...

Cheers

bandeiram

---

### Post by bandeiram on 2007-05-15
Anyone... please...

---

### Post by rillip on 2007-05-19
I would really recommend you post this in the networking forum.  They'll have more experience with this.  I would recommend a router as well, since connecting via ethernet is always easier than using a physical device, but that might add more confusion into the mix.

---

