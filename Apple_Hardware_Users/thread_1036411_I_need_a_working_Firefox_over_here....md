---
title: "I need a working Firefox over here..."
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by khelben1979 on 2009-01-10
Hello.

Since I have recently upgraded my Linux system from Debian Etch to Lenny my Iceweasel (Firefox) stopped working.

So now I decided to try a version of Firefox from rpmfind.net, but I didn't manage to get it working.

So now I need help on this. Anyone?

---

### Post by stream303 on 2009-01-11
Well, if you have all your bookmarks etc backed up, I suppose you could just try deleting your existing ~/.mozilla directory and starting it that way.

Or perhaps just go into synaptic and totally remove it that way and reinstall it.  Or get low level with dpkg --purge and then reinstall....

You may also want to consider taking a step even further than Debian, and go with GNU IceCat, which I see has just released 3.0.5:

[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

OOPS - I just saw that it was i386 only - no ppc - drats.

---

### Post by noriek on 2009-01-11
What's not working about it exactly?

If like me it's a difficulty with IPv6, type about:config in to the browser address field then search for ipv6 you'll get the entry "network.dns.disableIPv6"  Set the boolean value to true and then see if works. If this is the problem then your firefox-based browser should work after this but you'll still have difficulties with packet managers and other internet functions until you address the problem at a more general level.

Also read this:

[http://wiki.debian.org/DebianIPv6](http://wiki.debian.org/DebianIPv6)

It might help, unfortunately it's beyond me so I can't give you anymore with that.

If this is irrelevant please post further details.

---

### Post by khelben1979 on 2009-01-11
The Iceweasel web browser won't start anymore, that was why I tried the firefox web browser from rpmfind.net. When I started the new installation of firefox from an xterm it complained about missing GTK libraries, even though all of them are installed. *sigh*

I've tried everything I can think of and it ended with that I decided to install IceApe instead. Now I have a working web browser, at least.

YouTube videos also works inside the IceApe browser. Funny names they have decided to use b.t.w..

---

