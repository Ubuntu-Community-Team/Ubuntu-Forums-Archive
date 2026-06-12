---
title: "Blacklisting IPv6 broke Synaptic?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by unconquerable on 2006-07-20
I used the following methods to get my wireless internet working.  WHen I first installed Drake all I could do wirelessly was use Synaptic to download package... at fulll speed.  Now after blacklisting IPv6 I can use firefox (still not gaim) and synaptic is broken.

Here is what I did.

> Alright, it does seem that IPv6 does break wireless for some computers, and here's how to fix it (Thanks to SlowJet).
Code:

sudo gedit /etc/modprobe.d/aliases


Then scroll down to where you see alias net-pf-10. Comment out alias net-pf-10 ipv6, and add a few lines so it looks like this:

Code:

alias net-pf-10 ipv6 off alias net-pf-10 off alias ipv6 off #alias net-pf-10 ipv6


Save the file and restart your computer. This did it for me, and I hope the same works for everyone else! Good luck! 
[B][U][I][U]
and[/U][/I][/U][/B]

> Another way of speeding up your system is to reconfigure firefox by telling it NOT to use IPV6 either. This is what you have to do:

1. Enter "about:config" using the address field of Firefox.
2. Enter "ipv6" using the "filter" text field.
3. Right-click on the line that has just appeared ("network.dns.disableIPv6") and choose "toggle".
4. Restart Firefox.

This value of "network.dns.disableIPv6" must be "true" in order to have it disabled.

Now Firefox should run like a dream.


SUMMARY: After this
firefox works
gaim does not (never did)
synaptic does not download packages (did at one time) ](*,)

---

### Post by unconquerable on 2006-07-20
For anyone that is interested, Synaptic was fixes with:
> sudo apt-get update

Also, when I take out the first step fire fox still works.  Gaim is still MIA.

---

