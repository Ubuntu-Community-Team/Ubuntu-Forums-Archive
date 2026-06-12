---
title: "GnomeUI-WARNING : While connecting to session manager:
Aut
Authentication Rejected"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Aliarse on 2007-03-05
Having problems opening the system > administration options, networking, users and groups ect. They will open, but they don't show anything, and it seems like they just hang there doing nothing, i've uploaded a picture to show you what i mean.

I tried adding the users & groups icon onto the desktop to get the command it was using, and when i type it into the terminal, it spits out this error.

(users-admin:7086): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Anyone know whats going on here? It was working fine, and the only thing i've recently installed was wine, for using utorrent. :confused:

---

### Post by igknighted on 2007-03-05
I don't have an answer for why they don't work, but the Gnome-UI warning is normal.  It is just debug output on the terminal, not any kind of crash.  Any time I open a gnome app from the terminal I get that, but it typically opens fine.

---

### Post by Aliarse on 2007-03-05
Ok, thanks for that info.

Some of them will open, like system monitor for example, but the main ones (users,networking,and services) wont open at all. Really confusing me as it was working fine. :(

---

### Post by mohansoundar on 2007-06-29
I too have the same problem :( !!
I just changed few options in the System ->Administration -> login window and from there onwards, I'm getting this error !!

Apart from the above mentioned problems, I do get this error in any administration related actions, say while installing new applications through Synaptic Package manager or through terminal.

Does anybody know what the solution could be #-o

- Mohan

---

### Post by mohansoundar on 2007-07-01
And, i could spot out the problem vaguely.  Not sure if that was the problem
I had previously modified System->Administration->login window's general tab's session field as Gnome and previously it was 'Run XClient Script'

Once when I changed it, the problem is solved :D

- Mohan

---

