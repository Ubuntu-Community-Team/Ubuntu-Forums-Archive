---
title: "linux only sees www pgs already being viewed by xp"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-03-16
Hey all,

Thanks to all of you for your support on Linux - it really makes the transition much easier.

**Question**:  I am running XP and Linux off the same router using dhcp.  However, my Linux box can only access the www pages that my xp computer is currently viewing.  Wild, eh?  NE ideas?

gs

---

### Post by Gimbo on 2006-03-16
Sounds very odd. Do you get the "...could not be found" error pop-up on Firefox for the sites that don't work? How about email/instant messaging - can you connect with those?

---

### Post by guysmiley on 2006-03-16
You're quite right... very odd.

I no longer think it's an OS issue of any kind... more like networking.

**Specifically**: My Linux box sees only the pages in the root of what my xp sees.  So if my XP box is browsing Google, the linux box can browse anything in google.com/...

I haven't tried messenging but I suspect similar errors and, yes, I get the timed out error in FF.

gs

---

### Post by tronica on 2006-03-16
have you tried plugging your modem directly into the linux box, if that solves it then its with your router, maybe misconfigured?

---

### Post by Gimbo on 2006-03-16
I think it'll be helpful if you supply as much info as you can about your setup and the particular problem. I probably won't be able to help, but someone else might.

As far as I understand it, you've got

-Internet connection coming into your house
-Router
-One XP computer
-One Ubuntu computer

If you could flesh this out with any other hardware you're using - model numbers etc, that will probably be helpful.

What happens if the XP computer is off?
How about if you turn the power off to your router and turn it back on again? (You've no idea how often this has solved "could not be found" errors for me)

---

### Post by guysmiley on 2006-03-16
Thanks for the help, Gimbo.

I tried re-booting the router, Linux box, and XP box.  No good.

I tried calling tech support at d-link.  They don't support linux!?!?!?!?

I have a d-link 504T modem/router and a wireless d-link di-524.

DSL line comes in to the house and enters the 504t.  Port1 goes to XP box, Port2 goes to di-524 and Port3 goes to Linux box.

IPs are 192.168.1.4 for XP, 192.168.1.3 for Linux and 192.168.1.2 for the di-524.  DHCP is enabled on the modem/router (504T) and disabled on the di-524.  Everything pings fine from XP and from Linux (the linux ping list goes on infinetly...?).

Any help is greatly appreciated!!!!

gs :confused:

---

### Post by Lord Illidan on 2006-03-16
Very strange problem.
Can you try this: In firefox, type about:config in the URL bar.

Then, filter IPv6.

And set network.dns.disableIPv6  to true.

Maybe it might help.

---

### Post by guysmiley on 2006-03-16
Thanks for the help!!!  The ipv6=true solved the problem!!!!

This is why open source works!  Thanks so much!

Now, can you please tell me what ipv6 does and why it worked?

Thanks again!

gs

---

### Post by Lord Illidan on 2006-03-16
[quote=guysmiley]Thanks for the help!!!  The ipv6=true solved the problem!!!!

This is why open source works!  Thanks so much!

Now, can you please tell me what ipv6 does and why it worked?

Thanks again!

gs[/quote]

Erm, to be honest, I just quoted the standard response given when something goes wrong with Firefox on these forums, it was a shot in the dark, believe me..

Perhaps a search on [www.wikipedia.org](www.wikipedia.org) may help.

---

### Post by optotron on 2006-03-16
IPv6 is a new IP addressing sheme that was invented due to the deplation of available addresses in the current IPv4 sheme
IPv6 is gradually being inteplemented and is supported by some ISPs. It has 128 bits instead of 32

---

### Post by optotron on 2006-03-16
and i have no idea as to why this would be any problem.

---

### Post by guysmiley on 2006-03-17
Thanks for the replies, guys!

And, thanks for the 'standard response' to firefox issues.  I figured for sure it was a network/router issue as IPs were in question.  I had no idea FF could be configured for IPs itself!

I really appreciate the help!

gs  \\:D/

---

