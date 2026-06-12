---
title: "[SOLVED] Automatic IP exchanger"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by sebkinne on 2008-02-15
Hello Everyone,

i was just going to put up a request for a program (or a script).

I am running a game server, which requires the current ip to be posted into a world.conf document (on a certain point of the doc, the old ip). now i was thinking if there was a script that would:

1. kill the world server (executed by ./world, and running in a terminal)
2. paste my current IP into the .conf document (at the right place of course)
3. save 
4. restart the ./world
5. do this every 30mins - 1 hour

I beleave this could be a challenge for people here, but i would greatly appreciate the help.

Thanks and best regards,

sebkinne

---

### Post by ByteJuggler on 2008-02-15
A better solution would be if the game server allows you to specify a host name, instead of IP address.  Many servers do.  In which case, you can use DynDNS.org to keep your hostname/IP address in sync, and you then probably don't have to do anything with your game server at all.

What game server are we talking about, if I may ask?  Is the above suggestion definitely not possible with your game server?

---

### Post by sebkinne on 2008-02-15
well thats the problem.

the game server requres the actual ip, cos it is too stupid to read the dyndns host.
however, to access the server i use the dyndns.

its a WoW server btw.

Thanks,

sebkinne

---

### Post by ByteJuggler on 2008-02-15
So, just to confirm,  if you simply place the dns name instead of the IP address in the .conf, it doesn't work, and you've tried that?

---

### Post by sebkinne on 2008-02-15
yea, i tried that ^^

---

### Post by ByteJuggler on 2008-02-15
> **sebkinne said:**
> yea, i tried that ^^

OK I understand, I'll see if I can concoct some script for you to do that... :-)  Give me some time...

---

### Post by sebkinne on 2008-02-15
thank you very much, i really appreciate it : )

---

### Post by sebkinne on 2008-02-15
ah, also another thought, just if you feel like it, or know how:

i also need a script that will start the whole server, but when it crashes, it needsta be restarted...

duno if that is possible. would be cool..

but yea, thank you very much.


best regard,

sebkinne

---

