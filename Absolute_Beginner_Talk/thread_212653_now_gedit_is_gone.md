---
title: "now gedit is gone"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by dfor50 on 2006-07-10
I seem to be going down a spiral of broken dependencies and this is only my first week! First my printer dissappeared and cups had also gone with it. Managed to fix that but now gedit has gone. This is what I get when i try to install it (again):

gedit:
 Depends: libgnomeprint2.2-0 but it is not going to be installed
 Depends: libgnomeprintui2.2-0 but it is not going to be installed
 Depends: libgtksourceview1.0-0 but it is not going to be installed
  Depends: gedit-common (=2.14.2-0ubuntu3) but 2.14.3-0ubuntu1 is to be installed

Those libgnomeprint thingies are actually installed but they seems to be later version to the one gedit wants. Any ideas how to fix it?

---

### Post by dmizer on 2006-07-10
you must have removed something pretty essential to the system for this to happen, that or you didn't do a complete install.  you can't install ubuntu without gedit or cups (printing).

are you sure you don't already have gedit on your machine?  how about this ... do you have any sort of gui interface at all at this point, or do you just have a command line interface?

---

### Post by dmizer on 2006-07-10
been thinking about this a bit more ... what were you doing when you lost your printer in the first place?

something seemingly completely unrelated can still effect your cups system.  for example, removing the packages for bluetooth will break all kinds of things.

once your printer/cups was broken, what exactly did you do to regain it?

---

### Post by dfor50 on 2006-07-10
Thanks for the reply. The synaptic manager shows gedit as not being installed. The only part as installed is the gedit-common but when I try to install gedit the gedit-common is shown as "Depends: gedit-common (=2.14.2-0ubuntu3) but 2.14.3-0ubuntu1 is to be installed".

---

### Post by dfor50 on 2006-07-10
I was trying to get the printer to show up in a windows xp computer. I tried using samba and then lost cups. The printer icon also dissappeared from the administration section. I got it back but can't remeber how. I have been having a baaaad day.

---

### Post by dmizer on 2006-07-10
actually ... i usually don't suggest this because breaking and fixing your system is part of the learning curve.  in your case though, i'm thinking that your quickest fix will be to reinstall from scratch.

there may be a qucker way to completely refresh your install, but i don't know of it, and you could spend weeks (if not months) trying to recover everything individually.

i'm still not sure what might have been removed/changed in order to get to where you are now, but you might back track a bit and review what you were doing right around when you lost your printer.  if you happen to think of something (configuration wise) that you did around then, note it here and we may be able to tell you more.

but really, my hunch here is that you're going to save alot of potential linux-pattern-baldness by simply scrapping your current install and starting over (backing up critical data first of course).

---

### Post by dfor50 on 2006-07-10
I remember now - for some reason cups was showing as not installed. I had to reinstall it. The same thing has happenned to gedit.

---

### Post by dfor50 on 2006-07-10
I was getting the message "the cups server could not be contacted". The reinstall fixed that.

---

### Post by dmizer on 2006-07-10
strange ... how did you install samba?

---

### Post by dfor50 on 2006-07-10
I think samba was already going. Anyway, I think your idea of a re-install is a good one. Maybe I can find a guide to do this here. Thanks for the suggestion.

---

