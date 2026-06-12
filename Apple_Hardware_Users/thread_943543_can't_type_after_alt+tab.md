---
title: "can't type after alt+tab"
date: 2008-10-10
forum: Apple Hardware Users
---

### Post by bskerr on 2008-10-10
Hi everyone,

Installed Ubuntu 8.04 on new Macbook 4,1 yesterday. Almost everything works great. One strange problem is that often, if I switch away from a window with alt+tab, when I return to it I cannot type. Once I minimize and restore the window, it's normal again. This only happens with alt+tab (clicking on the bottom panel works normally). It happens occasionally with terminals and Firefox, but consistently with OpenOffice. Not sure if this is an Apple-specific problem, since other people seem to have posted similar symptoms.

Thanks in advance, and apologies if a solution has already been posted.

---

### Post by bskerr on 2008-10-13
Anybody else having this problem, or know how to solve it? As someone who likes to use the touchpad as little as possible, this is making things very inconvenient.

---

### Post by bskerr on 2008-10-29
Finally figured it out on my own: it was compiz. For anyone else experiencing the problems I described:

System->Preferences->Appearance
click on "Visual Effects"
set to "None"

Now (if anyone is reading this) why did compiz behave this way? Any way to fix the window switching problem without turning off compiz? Probably this thread belongs in "Desktop Effects & Customization".

---

### Post by cyberdork33 on 2008-10-29
try cmd+tab when compiz is enabled.

---

### Post by bskerr on 2008-10-30
You're right, cmd+tab doesn't have the same problem, although the animation is annoying enough that I don't see myself ever using it. Cyberdork, is this something you had seen before?

---

### Post by cyberdork33 on 2008-10-30
> **bskerr said:**
> You're right, cmd+tab doesn't have the same problem, although the animation is annoying enough that I don't see myself ever using it. Cyberdork, is this something you had seen before?

no, but CMD+TAB is the compiz window switcher.. I thought you might be able to use it instead (I often do because I am used to the OSX method of application switching). maybe there is an option that allows you to edit the animation in the compiz config tool

---

