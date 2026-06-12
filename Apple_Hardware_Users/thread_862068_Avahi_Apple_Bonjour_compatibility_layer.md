---
title: "Avahi Apple Bonjour compatibility layer"
date: 2008-07-17
forum: Apple Hardware Users
---

### Post by Kooothor on 2008-07-17
Hi, 

I was browsing my logfiles when I saw this :

> Jul 17 11:15:10 ktr-linux cupsd[5092]: *** WARNING *** The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
Jul 17 11:15:10 ktr-linux cupsd[5092]: *** WARNING *** Please fix your application to use the native API of Avahi!
Jul 17 11:15:10 ktr-linux cupsd[5092]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>

So I went there : [http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd](http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd)

and so.....
Can anyone do the port :mrgreen: ?

Thanks :)

---

### Post by cyberdork33 on 2008-07-17
you should probably file a bug against cups. or, there may be an update coming already, it just isn't in Ubuntu yet.

---

### Post by pxwpxw on 2008-07-17
Got the same warning with hardy ppc and printing to airport express base stn, thouhgt it might be cause of very slow responses.

CUPS attitude doesn't sound helpful:


The bug has been reported and got the dreaded "Fix Version Will Not Fix"
blames avahi.
[URL="http://www.cups.org/str.php?L2655+P0+S0+C0+I0+E0+M10+QApple+Bonjour%2Flibdns_sd"]
Bug Report - libdns_sd[/URL]

[http://www.cups.org/index.php]("http://www.cups.org/index.php")

---

### Post by cyberdork33 on 2008-07-17
> **pxwpxw said:**
> The bug has been reported and got the dreaded "Fix Version Will Not Fix"
blames avahi.
that doesn't really make sense since it basically said cups is using a legacy method of interaction...

---

### Post by pxwpxw on 2008-07-17
> **cyberdork33 said:**
> that doesn't really make sense since it basically said cups is using a legacy method of interaction...
Agreed.
What to do?

---

### Post by Kooothor on 2008-07-18
Ok, thanks for your responses, I guess I'll just leave it on....

---

### Post by ArcRiley on 2009-01-23
This is a summary of this problem:

cups, and other packages, are designed to be cross platform using the mDNSResolver library which is released as free software by Apple.

Avahi, which is not cross platform but is better integrated with Gnome, has built a crude compatibility layer to allow mDNSResolver apps to work with it, but it's developers have decided to pressure applications using Apple's API by printing a warning to their user's logs.

The proper fix is to remove the offending code from Avahi's warn.c in Ubuntu.

---

### Post by mastapat11 on 2009-06-11
> **ArcRiley said:**
> 
The proper fix is to remove the offending code from Avahi's warn.c in Ubuntu.

Or u can type ***"export AVAHI_COMPAT_NOWARN=1"*** at the command line (don't need sudo).
and that should stop the error messages. its not fix, but i don't think either side is about to budge anytime soon 

argh!!!   :mad:

---

### Post by JKyleOKC on 2009-07-16
> **mastapat11 said:**
> Or u can type ***"export AVAHI_COMPAT_NOWARN=1"*** at the command line (don't need sudo).
and that should stop the error messages. its not fix, but i don't think either side is about to budge anytime soon 

argh!!!   :mad:I'm sure that Apple, which now owns CUPS and maintains cupsd, isn't about to switch from their own API. Perhaps we should fork avahi for all the *buntu distributions, and remove the warning (or even improve the compatibility code if anyone is interested). I don't see how an "export" command at the CLI is going to survive a reboot and prevent the message from showing up again in the logs!

---

