---
title: "setup printer using localhost:631"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by rlutker on 2007-05-24
I have tried to setup my lexmark x73 using localhost:631 with no success.  My computers operating system is ubuntu dapper.  The printer is connected to a windows xp computer that is connected to my home network.  When I enter the information in the password dialog box and press enter,  Nothing happens except for another password dialog box pops up asking for the same information.  Please give detailed instructions as to what I am supposed to do to get my printer working for my ubuntu computer.
Thanks,
rlutker

---

### Post by wpshooter on 2007-05-24
rlutker:

I hope you have better luck on this than I did.  I gave up on trying to get this to work a good while back.  I am now in a holding pattern.

---

### Post by Dzenhax on 2007-05-24
The issue is probably with your username, and is a windows authentication issue.

Windows requires one of a couple of different formats.

Say the local computer is named Desktop

Username = username@desktop

but if you are on a domain (don't laugh, people do this at home) and the domain is DoMayne.com

then username should be [email]username@DoMayne.com[/email]

Work group may need to be @workgroup name, but I have never run into that one.  Usually local computer name (the windows box) works.

Dzen

---

