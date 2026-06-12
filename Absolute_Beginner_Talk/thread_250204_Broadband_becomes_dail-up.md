---
title: "Broadband becomes dail-up"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by navneeth on 2006-09-03
I never have had problems with making Ubuntu recognise the modem (ADSL). But the problem is that most of the time, the connection is very slow.In fact it never "moves" at all. And there are sudden bursts of speed, and then it goes back to being dead slow. I really feel like using a 56k connection. Is there a way to make it work properly, like it does when I'm using XP?

---

### Post by Sef on 2006-09-03
What kind of ASDL card do you have?

Have you checked System > Administration > Networking to make sure it is set up right?

---

### Post by Omnios on 2006-09-03
Not shure but I learnt that some isp's have special set ups for ntworked and apple and linux set ups. You might want to phone and ask your isp. I even heard a crazzy set uo where a user had to set up a special ip. Anyways its a start.

---

### Post by FuriousLettuce on 2006-09-03
Not sure if this will help, but it might be worth just disabling IPv6 - your slowdown could be caused by IPv6 lookups.

Type 'about:config' in firefox, scroll down to an entry called 'network.dns.ipv6disable' and double-click it to set it to true. Now check the net. If it's faster, it might be worth disabling IPv6 across the whole system. Do:

```
sudo nano /etc/modprobe.d/blacklist
```

and add 'blacklist ipv6' (without the quotes). Save the file (ctrl+x, then type 'y' for yes and press enter). Now, reboot your computer. Is the net any quicker?

---

### Post by alyson on 2006-09-03
> **navneeth said:**
> But the problem is that most of the time, the connection is very slow.In fact it never "moves" at all. And there are sudden bursts of speed, and then it goes back to being dead slow.

I'm having the same problem with a friend's laptop and it's quite maddening.  My laptop (also Ubuntu 6.06), however, works fine on the same connection.  Has anybody else experienced this and figured out how to fix it?

---

### Post by navneeth on 2006-09-04
> **Sef said:**
> What kind of ASDL card do you have?
An ethernet card, if that's what you're asking.

> 
Have you checked System > Administration > Networking to make sure it is set up right?[B]
Ethernet connection
The interface eth0 is active[/B]

[quote=FuriousLettuce]
Type 'about:config' in firefox, scroll down to an entry called 'network.dns.ipv6disable' and double-click it to set it to true. Now check the net. If it's faster, it might be worth disabling IPv6 across the whole system.[/quote]
I'll give that a try. Thanks.

---

### Post by navneeth on 2006-09-04
> **FuriousLettuce said:**
> Not sure if this will help, but it might be worth just disabling IPv6 - your slowdown could be caused by IPv6 lookups.

Type 'about:config' in firefox, scroll down to an entry called 'network.dns.ipv6disable' and double-click it to set it to true. Now check the net. 
Changin the value doesn't seem to help. :(

---

### Post by alyson on 2006-09-04
> **FuriousLettuce said:**
> Not sure if this will help, but it might be worth just disabling IPv6 - your slowdown could be caused by IPv6 lookups.

Disabling IPv6 hasn't helped me, either.

---

### Post by OldGaf on 2006-09-05
I found [this]("http://www.santa-li.com/linuxonbb.html") page helped me speed up my broadband a great deal.

---

### Post by alyson on 2006-09-07
I'm not sure if this will help you, but I was having a similar problem with my connection, and I fixed it by updgrading my router's firmware.  Of course, this won't be helpful at all if you aren't running through a router...

---

