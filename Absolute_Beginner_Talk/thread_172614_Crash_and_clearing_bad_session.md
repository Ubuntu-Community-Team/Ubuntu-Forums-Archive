---
title: "Crash and clearing bad session"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-05-09
I am experiencing periodic system freeze-ups that don't respond to any of the key combinations that are supposed to free things.

What is worse, in my view, is that after I power down and restart, the computer apparently attempts to load the dead session and hangs again.

So, newbie question: How do I clear all old session information before the desktop tries to load it again?

Thanks.

---

### Post by nalmeth on 2006-05-09
can you log into gnome failsafe session?
If so, then go to SYSTEM / PREFERENCES / SESSIONS
and delete the 'default' session

post result

---

### Post by aysiu on 2006-05-09
Both Gnome and KDE have options to **not** save your session at logout. In fact, so does XFCE.

---

### Post by jlhughes on 2006-05-09
[QUOTE=aysiu]Both Gnome and KDE have options to **not** save your session at logout.[/QUOTE]

I do NOT have a check next to "Automatically save changes to session" in System >> Preferences >> Sessions.  That's why I'm confused by the behavior of the system.

If I log off with windows open and restart, the windows are "restored" when I log in again.

I am assuming (note this is a beginner's post) that the same thing is happening after a crash: The system is attempting to open the windows and apps that were running when the system crashed.

This is a "feature" I want to be able to disable.

---

### Post by aysiu on 2006-05-09
Can you create another user and see if that user has the same behavior?

If so, there's something fundamentally wrong with your installation.
If not, your user profile is corrupted somehow.

---

### Post by nalmeth on 2006-05-09
> Both Gnome and KDE have options to **not** save your session at logout. In fact, so does XFCE. Strangely absent from Dapper-Gnome upon logout

Did you try to delete the 'default' session as I suggested?
I had a similar problem, and solved it this way.

In case you didn't understand, I meant to login from GDM, changing 'session' to failsafe gnome

---

### Post by jlhughes on 2006-05-09
[QUOTE=nalmeth]Did you try to delete the 'default' session as I suggested?
I had a similar problem, and solved it this way.[/QUOTE]

Just to see how it worked, I tried leaving some apps running and Firefox windows open and logged off and logged back on in the desktop failsafe mode (as opposed to standard failsafe or recovery mode.)

I didn't see a way to "delete" the default session or any previous session. 

Since I logged off and didn't just power off, this experiment didn't really simulate the conditions I've been experiencing.  The machine has been working well, with the exception of some graphic corruption, and I'm worried that simulating a crash will do more damage to files than it is worth.

Thanks for the help, though.

---

### Post by nalmeth on 2006-05-09
>  If so, then go to SYSTEM / PREFERENCES / SESSIONS
and delete the 'default' session
Saving your regular session won't save it for the failsafe sessions aswell, it's meant to be a 'neutral' gnome ground you can enter to help fix installation problems.

---

