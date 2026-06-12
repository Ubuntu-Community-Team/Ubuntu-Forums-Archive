---
title: "Same Problem as Before"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Listener008 on 2007-07-21
Ok I posted a thread about a problem I was having and got no answer so im posting it again so that maybe the right person will see it and be able to help me.... "Ok someone told me to press control alt and backspace and after I did all my effects stopped working.... how do i fix this?" Thats my problem... I already checked and the effects say that they're enabled... and I have already tried restarting my PC... Any other suggestions would be greatly appreciated

---

### Post by ddrichardson on 2007-07-21
You can add a bump posting to a previous post to re-raise its profile ;-)

Which "effects" are you using?

---

### Post by ravenwere on 2007-07-21
Ctrl +Alt+Backspace is a shortcut to restart your Xserver. It normally sends you back to your login screen where you have the options of starting KDE or Gnome etc. It is configured by the /etc/X11/xorg.conf file.

Have you installed additional software eg OpenBox to create these effects? If so you may have to select that type of session when logging in.

r

---

### Post by pyros on 2007-07-21
> **ddrichardson said:**
> You can add a bump posting to a previous post to re-raise its profile ;-)

Which "effects" are you using?

Actually, bumping makes it look like you are getting the answers you needed...

---

### Post by ddrichardson on 2007-07-21
I stand corrected ;-) but [SOLVED] looks even better!

---

### Post by pyros on 2007-07-21
The first thing that I would do would be to disable the effects, restart and try re-enabling them. I would not recommend using ctrl+alt+backspace to restart x, as it is hardly freindly to any programs that may be using x at the time. instead, just log out and back in again, that will restart x if your gdm settings are still set to the ubuntu defaults.

---

