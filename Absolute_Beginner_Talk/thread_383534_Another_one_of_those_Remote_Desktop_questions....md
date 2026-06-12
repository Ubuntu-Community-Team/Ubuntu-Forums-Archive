---
title: "Another one of those Remote Desktop questions..."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by TehSnarf on 2007-03-13
Alright, I'm trying to set up a remote desktop box (home) and access it from work (work), and as far as I know, everything should be set up correctly (but I doubt very much that it is, since it's not working). What I'm doing, right now, is I've installed openssh, that seems to be working fine, I've enabled (again, I think) Remote Desktop, and I've got ddclient up and running.

I'm at work right now, so I was curious is there anything that I can do via command line at work to the home box to get this working? Config files or something somewhere?

---

### Post by solar george on 2007-03-13
What do you mean remote desktop, if you mean that you have enabled remote login in the login window set-up you will need to use an Xwindows system to connect. Try [cygwin/X]("http://x.cygwin.com/") and [these instructions]("http://x.cygwin.com/docs/ug/using-remote-session.html")

---

