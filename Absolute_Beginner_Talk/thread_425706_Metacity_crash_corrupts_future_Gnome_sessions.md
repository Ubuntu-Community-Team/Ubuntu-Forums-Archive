---
title: "Metacity crash corrupts future Gnome sessions"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-04-27
I'm experiencing this bug: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350) also opened upstream at [http://bugzilla.gnome.org/show_bug.cgi?id=433253](http://bugzilla.gnome.org/show_bug.cgi?id=433253)

Here is the comment on Bug 433253:

> Comment #1 from Elijah Newren  (metacity developer, points: 26)
2007-04-25 17:21 UTC [reply]

Ooops!  Yeah, this crash is my fault.  I introduced it in svn revision 3137, as
a "simple cleanup" to src/session.c.  Basically, metacity is guaranteed to
crash at session-save time whenever there are any programs running that don't
support session-saving (e.g. emacs and half a zillion other old apps out
there).  The fix is pretty simple, so I'll mark this as a gnome-love bug.


I've only had Ubuntu installed for a few days now so I would love some advice.

Here are some comments on Bug 106350:


>  Sebastien Bacher said on 2007-04-25: (permalink)

Thank you for the work on the bug, I've opened one upstream on [http://bugzilla.gnome.org/show_bug.cgi?id=433253](http://bugzilla.gnome.org/show_bug.cgi?id=433253)
 Sebastien Bacher said on 2007-04-25: (permalink)

The changes has been suggested by upstream and works correctly on my desktop
 Sebastien Bacher said on 2007-04-26: (permalink)

    [* correct debdiff now]("http://librarian.launchpad.net/7409469/metacity.debdiff")

 Sebastien Bacher said on 2007-04-26: (permalink)

the update has been approved by Martin on IRC while launchpad was down, I've uploaded it

At the debdiff link above, it mentions something about a patch, but I don't really understand it.

So, am I able to get this bug fixed on my computer (not just a workaround), and if so, how do I go about doing it?

Many thanks,
Trisha

---

