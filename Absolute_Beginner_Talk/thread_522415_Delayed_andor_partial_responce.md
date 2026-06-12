---
title: "Delayed and/or partial responce"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-08-10
I really like how in Ubuntu, you really never have to reboot like windows, but certain things, like changing the mouse cursor, aren't quite perfect yet.  For example, if I was to change my cursor, in certain apps, like Firefox, the change would take effect immediately, but for other apps and the rest of the system, that requires you to log-off and then back on (if I remember KDE correctly).  Why is it that an OS of this quality has some trouble with that, but even windows can do this perfectly?

Of course on the other hand, windows takes a good 5 seconds to switch to a new theme, but Ubuntu does it pretty much on click!  And in most cases, the difference between themes isn't just colour, but totally new everything! :)

---

### Post by ddrichardson on 2007-08-10
Although its not an OS issue with cursors - its an Xorg issue, I must confess the cursor thing has always annoyed me. There are so many glitches in it - like you say having to restart the server (although this may be to avoid using a shared memory area which are prone to security issues).

The one that really gets me is when you change a cursor and its the new one in apps like firefox and the old one on gnome desktop.

---

### Post by ryanVickers on 2007-08-11
> 
The one that really gets me is when you change a cursor and its the new one in apps like firefox and the old one on gnome desktop.

Yes, that's what I mean!  And I guess the rest of that makes sense, but no ideas as to a fix?  Not that this is really an emergency though,.. :p

---

### Post by ddrichardson on 2007-08-12
Its wierd - I guess I should have looked into it more - still used to other distros. When I install to /usr/X11R6/lib/icons they only work with X apps - not Gnome. When Iinstall to /usr/share/icons and select through theme manager they change without restarting the X server.

---

### Post by ryanVickers on 2007-08-12
My cursors are in there though...

I've been thinking for a while and can't come up with a single reason why if it's able to change right away for some apps, it shouldn't do it for all of them!  It really would make more sense to be kind of "all or nothing".

---

