---
title: "GTK Theme, Borders And Scrollbars won't change"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by gidra on 2007-06-06
I've just install Mac Osx Bundle from gnome-look.org but the scroll bar and control items won't change. I already once had this problem, solved it by install pixbuf. Now i dunno what to do. Any ideas please?

---

### Post by empthollow on 2007-06-06
doesn't sound like the exact same problem i've had but i had to install a particualr gtk-engine to get certain themes to show up correctly. good luck.

---

### Post by gidra on 2007-06-07
I installed all gtk-engines in synaptic but no luck. Please any help with this annoying problem?

---

### Post by gorbay on 2007-08-26
I'm having the same problem and it's getting more and more annoying every day. Nevertheless, after installing beryl and xgl, I've been encountering troublesome error messages from gnome panels... ](*,)

---

### Post by Dark Star on 2007-08-26
Same problem here.. Thats why have started using Metacity/emerald themes :(

---

### Post by gorbay on 2007-08-26
Unfortunately MetaCity / Emerald didn't solve it for me. window borders and effects are just great but the application controls ( buttons, scroll bars ... ) are simply not.

---

### Post by Wolki on 2007-08-26
Check your home directory for a hidden file named ".gtkrc-2.0". If you have one, open it. Themes and settings specified there will sometimes override the ones selected via the theme settings applet, so that cahnging them via the grapic tool will not work correctly. If it contains stuff like that, comment it out, or rename the file and see if it will work then.

If that's not the problem, it may be engine-related - Even if all engines from the repos are installed, there may be some that are so new that they aren't included yet. Open the theme in the archive manager and open the file "gtkrc". Search for the line that starts with "engine", and see the next word for the name of the engine it uses. If you don't have this engine, you'll need to install it before you can properly use the theme.

---

### Post by gorbay on 2007-08-26
Thanks alot! The problem was that the theme was using an GTK2+ engine that I didn't have. The problem is no more :)

---

