---
title: "Make &quot;Failsafe Gnome&quot; the default session for one user"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Sico on 2007-10-23
I have 3 users on my system.  I am having stability issues with compiz, but am working on it little by little and making progress.  The other two users do not need compiz / eyecandy.  Is there anyway I can make the other two accounts login to "failsafe gnome" by default?  I know I coule remove xserver-xgl, but then I can't tinker with compiz.  Even if I could make "failsafe gnome" the default session and choose another session when I want to play around with eyecandy.  Any suggestions?

---

### Post by cameronw on 2007-10-23
When you select an option other than the default a dialog asks you whether to make it default or "just for this session".

---

### Post by Sico on 2007-10-24
Yes, it does for other sessions...  but it does NOT for "failsafe gnome"  :(

---

### Post by cameronw on 2007-10-24
Oh I see. Could be because that session is not in /usr/share/xsessions. Neither is Failsafe Terminal. I'm not sure on that one.

---

