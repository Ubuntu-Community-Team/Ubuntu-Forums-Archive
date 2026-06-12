---
title: "why firefox is slow"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-12-29
firefox is slow when compared with epiphany. i switch on ff and epiphany and resize them side by side. i click a link on them at the same time [almost] and epiphany is always faster them ff on every link [1 to 3 seconds i think?] also my firefox sudden close [all firefox windows!] when visiting site which has flash.

---

### Post by jrharvey on 2007-12-29
I actually use firefox for wine. It is faster than anything for ubuntu. Its reallly weird.

---

### Post by Dr Small on 2007-12-29
The problem with flash, is most likely due to not having proper plugins to handle flash, and the slowness of Firefox could be from lots of extentions (?).

Dr Small

---

### Post by JillSwift on 2007-12-29
I found Firefox really got better when I turned off IPv6. THe problem with IPv6 is, for most, that it's unroutable. So, it tries the IPv6 lookup or address, times out, then tries IPv4. All these delays on a page with a bunch of elements means very noticable delays while surfing.

To turn off IPv6:
Type ***about:config*** in your url bar.
In the "filter" bar that appears on that "page", type ***IPv6***.
Set network.dns.disableIPv6 to [I][B]True
[/B][/I]
Restart Firefox and vaboom, improved performance.

---

### Post by Kosimo on 2007-12-29
> **afeasfaerw23231233 said:**
> firefox is slow when compared with epiphany. i switch on ff and epiphany and resize them side by side. i click a link on them at the same time [almost] and epiphany is always faster them ff on every link [1 to 3 seconds i think?] also my firefox sudden close [all firefox windows!] when visiting site which has flash.

I'm having exactly the same behavior than you. Slow, and unstable (sometimes close suddenly)
I'm still asking myself why I keep using it...   
The answer is.. Extensions ;)

Would love to install extensions in Opera.

---

### Post by Dr Small on 2007-12-29
> **JillSwift said:**
> I found Firefox really got better when I turned off IPv6. THe problem with IPv6 is, for most, that it's unroutable. So, it tries the IPv6 lookup or address, times out, then tries IPv4. All these delays on a page with a bunch of elements means very noticable delays while surfing.

To turn off IPv6:
Type ***about:config*** in your url bar.
In the "filter" bar that appears on that "page", type ***IPv6***.
Set network.dns.disableIPv6 to [I][B]True
[/B][/I]
Restart Firefox and vaboom, improved performance.
That was awesome! It helped me out :)

---

### Post by Joeb454 on 2007-12-29
Tried what JillSwift said to do, and I have noticed a bit of a performance gain

---

### Post by Kosimo on 2007-12-29
> **JillSwift said:**
> I found Firefox really got better when I turned off IPv6. THe problem with IPv6 is, for most, that it's unroutable. So, it tries the IPv6 lookup or address, times out, then tries IPv4. All these delays on a page with a bunch of elements means very noticable delays while surfing.

To turn off IPv6:
Type ***about:config*** in your url bar.
In the "filter" bar that appears on that "page", type ***IPv6***.
Set network.dns.disableIPv6 to [I][B]True
[/B][/I]
Restart Firefox and vaboom, improved performance.

Amazing...

Where did you learn this?


It works for me!

---

### Post by methodical on 2007-12-29
wow thanks JillSwift!

---

### Post by jonnywombat on 2007-12-29
If you like Firefox, want extensions and a bit of extra speed then try swiftweasel.. I use the 32bit edition for my amd64bit install and it really flies...

You can download it via synaptic, or if you add it's repo then your good to go for updates...

Visit for more info [http://sourceforge.net/projects/swiftweasel](http://sourceforge.net/projects/swiftweasel)

To install 32bit edition on 64bit ubuntu visit [http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+3in1+installer](http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+3in1+installer)

Jonny

---

### Post by clayts450 on 2007-12-29
Just to add my support to the IPv6 hack - I did it yesterday and Firefox flies now :)

---

### Post by afeasfaerw23231233 on 2007-12-30
well it really runs a bit faster! thanks . but i once heard of ipv6 is a new type of ip address which runs 128 bit [which is something like ae:12:a2:e1:12:32. i can't remember] would ff fail to browser those sites with ipv6?

---

### Post by Joeb454 on 2007-12-30
It probably would yes, but then you can change the about config again anyway :)

Plus IPV6 hasn't really taken off yet, though I'm sure there's plenty of small-time sites out there using it

---

### Post by JillSwift on 2007-12-30
> **afeasfaerw23231233 said:**
> well it really runs a bit faster! thanks . but i once heard of ipv6 is a new type of ip address which runs 128 bit [which is something like ae:12:a2:e1:12:32. i can't remember] would ff fail to browser those sites with ipv6?Wouldn't matter unless your NAT (if you have one) and local ISP can route IPv6 anyway. And if they could, turning off IPv6 wouldn't have sped up Firefox for you.

Right now getting to the relatively few places that have gone to IPv6 is easy as they're running IPv4 in parallel. Yay backward compatibility =^_^=

---

