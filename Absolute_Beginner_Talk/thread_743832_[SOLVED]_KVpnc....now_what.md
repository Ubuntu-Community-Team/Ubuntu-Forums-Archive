---
title: "[SOLVED] KVpnc....now what"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by fatmano on 2008-04-03
Ok so after some yelling, screaming and gnashing of teeth, I am able to get what appears to a connection to my vpn via pptp.  KVpnc says that I am connected and when I hover over it in the system tray it shows a tunnel IP address.

Now that I am connected I want to ssh to a specific IP address.  I thought all I would have to do is :
ssh <username>@<ip>

but this does not seem to work.  It accepts the command but never comes back.

What am I doing wrong.

TIA

---

### Post by fatmano on 2008-04-03
Ok...some new data....I decided that I would reboot just to see what would happen and now I get

ssh: connect to host 10.0.1.150 port 22: No route to host

do I need to add something to my routing tables?

---

### Post by fatmano on 2008-04-03
How do I set a route to the machine?  Do I need to do some sort of tunneling on the ssh command?

ssh -L 22:10.0.1.150:22 

or something like that?

Any help would be great.

TIA

---

### Post by fatmano on 2008-04-04
Ok so I got it....after a lot of trolling on the interwebs I found some networky stuff and it seemed to apply to me.

Under networks I had to add the ip address that I wanted to go to or at least a portion of it and also the device to send it out on.

So I went back and edited my working connection Settings > Configure KVpnc

Under the Network > Routes selection on the left I checked the "use addition network routes"  ( the drop down still reads Keep default route )

I added the ip address that I wanted to go to...in my case it is 10.0.1.150
so I added 10.0.1.0 /24  

This is the networky thing that I did not realize.  The /24 or netmask of 24 says use the first 3 octets ie 10.0.1 and let anything else go.  If I wanted the full address it would be 32.

Then chose the device of ppp0 and viola....I am able to get to my remote box thru a M$ pptp vpn.

Hope this helps someone else.  There was no activity on this post other than myself, so maybe everybody knows this or I am the only one that this has ever happened to.

-eo


now how do I mark it as solved?

nevermind...I found how to mark it

---

