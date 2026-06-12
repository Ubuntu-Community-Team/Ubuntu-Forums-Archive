---
title: "Keyboard layouts"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Corvair on 2006-04-24
Hello everyone,
I would like to install the Canadian multilingual keyboard. I tried using Synaptic but I keep gettin the US layout. I need to write in both english and french, so what is the solution?  ](*,)

---

### Post by Qrk on 2006-04-24
You shouldn't need to use synaptic.

System->Preferences->Keyboard->Layouts->Add->Canada->Multilingual

---

### Post by Corvair on 2006-04-24
Thanks for your reply,

I tried this already but it does not work.
It shows me the proper result but it does not get implemented.

---

### Post by Hygelac on 2006-04-24
Do you have access to both GNOME and KDE (or something else for that matter)?  I found that I could not get GNOME to recognize my «Canadian French» keyboard layout, although KDE would.  That said, I am sure that there are French GNOME users, so maybe you will want to learn what it is that they do in this situation.

---

### Post by Corvair on 2006-04-24
Here is something that may help you understand the problem.
What can I do to solve this?


Error activating XKB configuration.
This can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

