---
title: "GNOME and KDE"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2005-12-06
How does this work, exactly?  I am vaguely aware that I can have both on my system (or Fluxbox or whatever else).  So let's say Pete installs KDE.  Then what?  Can I switch in the middle of a session, do I have to log out, what's the deal?

Sorry if this seems elementary, but coming from windowsland, the concept of multiple windows manager options just boggles me.  So naturally, I want at least two or three, just because I can ;-)

---

### Post by aysiu on 2005-12-06
Generally, you have to log out, but I think there's something call xnest that allows you to have a KDE session within a Gnome session and vice versa.

---

### Post by GreyFox503 on 2005-12-06
Most of the time, to switch environments, you can log out and then log back in to a different one.  However, if you want to run two at the same time, you can.

In Gnome, go to Applications > System Tools > New Login.  This will bring you into a new virtual terminal at the login screen, where you can choose a different desktop environment.

If you aren't familiar with virtual terminals, you switch between them by holding Ctrl, Alt, and then pressing one of the F-keys.  Normal GUI sessions run on F7.  Try pressing Ctrl + Alt + F2.  It should bring you to a new terminal shell, waiting for you to login.  Hit Ctrl + Alt + F7 to come back to Gnome.

Now, if you do the above method for making a second graphical session, it should put it on F8.  Then hit Ctrl + Alt (F7 or F8 ) to switch between them.

To end your new session, just go to "log out" or the equivalent in the environment, and then it will exit and bring you back to your other desktop.

---

### Post by TeeAhr1 on 2005-12-06
Thx, guys!  (Notice how the "this doesn't work" questions are getting fewer and fewer and the "how do I make these other things work too" questions are getting more and more?  I like that.  I like it a whole lot.)

---

### Post by GreyFox503 on 2005-12-06
[quote=TeeAhr1]Thx, guys!  (Notice how the "this doesn't work" questions are getting fewer and fewer and the "how do I make these other things work too" questions are getting more and more?  I like that.  I like it a whole lot.)[/quote]

I remember how it felt when I reached that point not too long ago.  I stopped spending time "making it work" and started to explore and see "what else can I do?"  This is where Linux gets fun and pays off. :)

---

