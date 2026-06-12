---
title: "Trouble with GDM setup"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Domie on 2007-05-08
> **delphiguy said:**
> Ok never mind I just found it at System Settings -> Advanced -> Login Manager

Well, good topic...

Because this login manager does not respond:
```
domie@PC:/$ sudo gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Kon het configuratiebestand van GDM niet benaderen.
domie@PC:/$ 

```

That last line says: could not approach the config file of GDM...

Is there a way to override this? I edited /etc/X11/gdm/gdm.conf:
```
AutomaticLoginEnable=true
AutomaticLogin=domie
```

But this doesn't work...

Someone an idea?

---

### Post by Domie on 2007-05-08
Ps: 6.10...

---

### Post by aysiu on 2007-05-08
Two things:

1. This is a separate issue altogether and won't solve your problem, but you should use *gksudo* (not *sudo*) with graphical applications. Read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

2. I've seen this problem come up several times on these forums, and A) I've never seen any explanation for why it occurs and B) I've never seen a working solution to it... ever. I've searched all over the internet, too.

The only "solutions" I know of for this error message are clean reinstalls or the use of an alternate display manager (KDM, WDM, XDM).

---

### Post by Domie on 2007-05-08
Well, this worked... Thanks.

---

### Post by aysiu on 2007-05-08
Which worked? Using a different display manager?

---

