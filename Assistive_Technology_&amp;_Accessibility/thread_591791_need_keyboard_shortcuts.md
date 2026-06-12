---
title: "need keyboard shortcuts"
date: 2007-10-25
forum: Assistive Technology &amp; Accessibility
---

### Post by justdude on 2007-10-25
I am setting up a computer for my wife using gutsy she's blind and we found that keyboard shortcuts is an easy way for her to use comp.
have rhythmbox player web volume and evolution set through prefferences keyboard shortcuts but how do we set up ones for movie player wordprocessor etc. any help would be appreciated.

---

### Post by justdude on 2007-10-27
I have shortcuts for rhythmbox but need to go from its library to radio stations that I have programed in it have looked everywhere can't find the keys.

---

### Post by kidders on 2007-10-28
Hi there,

Assuming you're not already using it, I would suggest taking a look at KDE and its media players & other apps. Although there *may* be some gaps in it from an accessibility perspective, I can't help feeling like dcop would provide a pretty clean general solution to keyboard shortcut problems.

Dcop allows you to interact directly with applications & their interfaces from the CLI. I use it quite a lot, by chaining sequences of dcop calls together in little scripts & binding them to keystrokes. In theory at least, you should be able to gain pretty arbitrary control over a KDE-based graphical environment that way ... If an application happened to be missing a particular shortcut for no good reason, you could essentially create one.

As far as media players go, mplayer comes to mind as something that might meet your wife's requirements.

---

