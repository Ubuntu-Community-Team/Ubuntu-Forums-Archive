---
title: "Deluge low upload rate after Firestarter"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by sphm on 2007-10-24
Hello all,

I've been using Deluge for a long time, but recently I installed Firestarter and now I'm getting really low upload rates (something about 2 or 4 kb/s).
I did some tests and it seems to be related with the firewall, when Deluge is closed iptables blocks just a few connections, when it's oppened iptables acts like a machine-gun.
Looking for the blocked connections list, they come from the most diferent ports as possible.   i think that's not reasonable to open all the doors for connections, so what's the point about using a firewall?

Someone knows how to solve it?

thxx

---

### Post by Seisen on 2007-10-24
You need to open the ports for deluge on firestarter. To do that go to the policy tab, then you need to right click on the second section under that tab that says Allow service|Port|For and select Add Rule. 

Next you either need to enter the port number or select bittorrent depending on what port numbers are used by deluge. If it is more than one port number than just enter like 6881-6889 then make sure anyone is selected then click add.

---

### Post by sphm on 2007-10-24
Well...
I Have already did it, port 6881-6889 are open, also 49152, 49153, 50212, and I also pressed "apply police" before a I set the ports.
Even with all those ports, it seems not to be enought, as I mentioned in my previous post, connections comes from too many diferent ports

---

### Post by Seisen on 2007-10-24
What does it say when you run the port test in deluge and do you have a router?

---

### Post by hyper_ch on 2007-10-24
sphm:

Firestarter is nothing but a graphical front-end configuration tool for iptables. whether Firestarter is running or not does not have any effect.

---

### Post by sphm on 2007-10-24
Seisen:
The test port says that the door is open.
See, the connections that iptables is blocking are comming from diferent ports that 6881-6889.
It doesn't happen when deluge is closed, so, it just can be other users trying to download from me, right?

hyper_ch:
I know what is firestarter and what's a front-end, thxx :-)

---

### Post by Seisen on 2007-10-24
Correct, some people set thier bittorrent clients to use different ports than those and also set them to use random ports.

---

### Post by hyper_ch on 2007-10-24
As you know what firestarter is then you also know that having it installed has no impact on deluge as long as you don't alter settings. So the problem has to be somewhere else...

Are you a Comcast user?

---

### Post by sphm on 2007-10-24
Well, it has a impact on deluge, specially if don't allow the service on specified door for listening.
What is happening is that lots of connections for upload are comming in different doors than that I allowed (6881-6889 as some others) so iptables block then.

The question is: the olny way to allow those conections is to open all the doors on iptables? and consistently make it useless.

Or there is something else to do?

thxx

---

### Post by sphm on 2007-10-24
...and I don't use comcast ;-)

---

