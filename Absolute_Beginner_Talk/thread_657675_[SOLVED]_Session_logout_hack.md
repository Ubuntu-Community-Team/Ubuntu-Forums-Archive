---
title: "[SOLVED] Session logout hack?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Achilles283 on 2008-01-03
I am sure there is a simple solution to this, but I have had no luck finding one via Google.

Is there a way to force Ubuntu to stay logged in indefinitely?  For example,  if I don't touch the computer for a certain amount of time, Ubuntu logs out and returns to the login screen.  I have many applications running that I need access to regardless of keyboard/mouse activity and I lose access once it goes to the login screen.

Any ideas out there?

---

### Post by shad0w_walker on 2008-01-03
Ubuntu doesn't automatically log out. It certainly isn't a default option. It sounds like something is crashing out randomly and causing you to log out.

---

### Post by Achilles283 on 2008-01-03
Wow, thanks for the quick response... that explains why I couldn't find anything at all concerning the issue on Google.  I'll check my logs and see if I can find out what's happening. Thx again!

---

### Post by shad0w_walker on 2008-01-03
Let us know what you find and hopefully we can help you sort things out. Good luck.

---

### Post by Achilles283 on 2008-01-04
Problem solved!

The logs showed the following error:

gdmgreeter[9069]: WARNING: Theme broken: must have pam-message label! 

Turns out I had a bad theme installed and every time the screensaver tried to fire up, the X display would crash.  Switched to a different theme and all is well.

Gotta love Ubuntu, troubleshooting has never been so easy.  Helps that I'm an uber-geek and can't get enough this stuff as well ;)

---

### Post by shad0w_walker on 2008-01-04
Congrats on solving the problem. Might want to mark the thread as solved.

---

