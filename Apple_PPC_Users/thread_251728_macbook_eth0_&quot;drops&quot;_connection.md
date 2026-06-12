---
title: "macbook eth0 &quot;drops&quot; connection"
date: 2006-09-05
forum: Apple PPC Users
---

### Post by sekre on 2006-09-05
Hello fellow Mac users!

I seem to have a problem that is probably too hard for me to solve by myself.
It seems that when I use my ubuntu install, my ethernet card "drops" connection every 5-8seconds or so.

For example, if I would do a ping to some server. And also try to download a file, the file will fail after some seconds with a Connection timeout error (sorta) while my ping will go without problems. No lost packages there or anything.

This problem is on MacBook (2.6.15-26 SMP) using dapper with all updates.

I feel this could prove to become a great problem, since I can't even donwload stuff from apt without it "dropping".
NOTE.  Sometimes it works for some minutes if I'm lucky.
NOTE2. Not only downloads, but internet and webradio is also affected.

I hope someone out there know how to fix this problem =)

---

### Post by sekre on 2006-09-07
okay this seems pretty wierd indeed. After we tweaked around with our router abit, it seems to be abit more stable. But still drops connection like before. And like before ping still works,

[http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml) -- This guy reports a problem with the sky2 module causing problems that seem to be like mine, however he also reports it fixed by dapper team.

But not sure...Don't know how to unload the module, but gonna find out and try and report back. Just in case someone else has this problem..

EDIT : That didn't do much good I'm afraid..
I'm kinda out of ideas myself. Anyone have a clue?
Anything at all, really.

---

### Post by Astrophobos on 2006-10-17
maybe it's related with this

[http://bugzilla.kernel.org/show_bug.cgi?id=6839](http://bugzilla.kernel.org/show_bug.cgi?id=6839)

I also experience this problem.

---

### Post by tyl on 2007-01-06
While I'm unsure whether or not this belongs in PPC, I've been wrestling this problem and haven't come up with a solution.  Just to clarify, I can browse fine, but when downloading files, the connection begins around 20 kb/sec and slowly shrinks to 5k or so bits/sec, dies and fluctuates from there on.  This problem makes it impossible to update ubuntu unless I want to wait forever at 500 bits/sec.

Occurring in a 2Ghz Macbook, pretty early generation (not Core 2).  Has anybody solved this somehow?  I'm using the sky2 module, which worked out of the box, which was really quite nice, aside from the ugly dropped connections.  This happens with both wireless and wired.

---

