---
title: "BadGC (invalid GC parameter)"
date: 2007-03-08
forum: Assistive Technology &amp; Accessibility
---

### Post by Riad on 2007-03-08
Did a search and found nothing. 

Is there absolutely no resolution for this Error?

I have this UML modeling tool and every time I click on the property tab for a particular component, the application dies and I get the following error in the error log file:

"X11 -    0 - BadGC (invalid GC parameter)"

My assumption is this has to do some thing with the X windows stuff? Did a Google on this but not much info there.  

Can any one out there help?:( :(

---

### Post by Riad on 2007-03-08
I also get the following errors:

X11 -    0 - BadWindow (invalid Window parameter)

and

X11 -    0 - BadAtom (invalid Atom parameter)

---

### Post by Riad on 2007-03-17
So no solution to this huh?

---

### Post by lloyd_b on 2007-03-17
BadGC doesn't ring any bells (but them I'm not a low-level X programmer).

BadWindow *does* ring a bell - it's what you get when an application references a window ID that doesn't exist.  BadAtom is something similar.

In short - the problem lies with your UML modeling program.  You should post this to their tech support (if it's commercial) or their support forum/dev list (for open source).

Lloyd B.

---

