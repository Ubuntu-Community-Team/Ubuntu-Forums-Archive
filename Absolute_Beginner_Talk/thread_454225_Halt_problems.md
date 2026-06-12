---
title: "Halt problems"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by hrsvan on 2007-05-25
After shutting down my kubuntu resets to default or sometimes even makes corrupted files...!
When using x to shut down the computer it turns the monitor off and I have to force the computer to turn off. only thing that seems like shutting down properly is 'sudo halt' in the commandline. But this only helps the computer to turn off by itself - it still resets to default next time I log in. (two desktops and no apps running)

I don't know what to try, might start out by logging the halt procedure and see where it stops. But how to do this?
And any other ideas?

---

### Post by Pragmatist on 2007-05-25
Two questions:

1.) What happens if you reboot?

2.) What happens if you logout and then shutdown from the display manager?

---

### Post by hrsvan on 2007-05-25
If I reboot, the same thing pretty much happens; cant do it from the x, but works allright from the console. but none of these saves my changes to the system.

I have not tried logging out and I can't try it out right now, unfortunately, since I'm out for the weekend. But as I recall, if I do not log in and makes it shutdown from x it works. But the few times it has worked shutting down from x I can't see the progress with the blue bar getting black. This I can see if I use the console...

---

### Post by Pragmatist on 2007-05-25
I don't use KDE, I use GNOME.  However, in Synaptic I see that the 2 packages that are probably responsible are these:

[B]ksmserver
kshutdown[/B]

**ksmserver** is responsible for restoring your session, so I would definitely try reinstalling it.   I would try reinstalling both packages, in fact.  Especially if you haven't already checked for updates to your system.

---

### Post by hrsvan on 2007-05-28
wierd,
It seems like the kshutdown wasn't even installed, but I did both reinstalls together with updates for the rest of my system. and now it seems to work just fine (for now)
thanks mate :)

---

