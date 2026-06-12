---
title: "set automatic/idle logout?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-03-22
How can I set Ubuntu to log out after 5 minutes of inactivity?

I read something about editing the /etc/bashrc and setting the timeout variable.

I am still pretty new and don't like getting into those files too much. I got in there and got scared =)
Any other way to do it?

I don't just want it to sleep, like in Power Management, but I want it to log the user out.

I know its probably easy, but I just can't seem to find it.

---

### Post by RealPSL on 2008-03-22
I believe what you are making reference to is the TMOUT variable that can be added to /etc/profile or /etc/bash.bashrc. This will only work for terminal logins but will not work for GUI sessions in KDE, GNOME etc.

---

### Post by bruce89 on 2008-03-22
Having the user log out when idle in a DE seems mad. What happens if they have an unsaved document opened?

You can have the screen lock when idle by going to the screensaver preferences.

---

### Post by TJCIB on 2008-03-22
When in a school, you have to weigh risks.  Only certain people are permitted access to the computers.  Many people forget to log out, leaving the computers wide open for another person.  Often this is the teachers leaving their grades, personal info, etc. open for people.

I appreciate the concern.

---

### Post by RealPSL on 2008-03-22
The same problem exists on other operating systems and for the most part administrators enforce a short idle time before the screen saver locks the screen. This is obviously not fool proof but it is better than nothing. Proper education about computer security might help as well.

---

### Post by Oldsoldier2003 on 2008-03-22
> **RealPSL said:**
> The same problem exists on other operating systems and for the most part administrators enforce a short idle time before the screen saver locks the screen. This is obviously not fool proof but it is better than nothing. Proper education about computer security might help as well.

Agreed locking the screen is a better solution in that it prevents unnecessary data loss from a forced logout. But with that said, if the system admin wants to enforce a forced logout policy its on his head when data loss occurs.

---

