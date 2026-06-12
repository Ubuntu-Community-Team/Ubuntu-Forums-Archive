---
title: "Ubuntu Freezes just before Splash Screen"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Alex6969 on 2006-08-27
Ok so yesterday i was messing around with xsession. well now when i try and boot ubuntu it loads everything like normal (where it says "Ubuntu" and has the progress bar) it finishes loading everything, but then when it sapposed to go to the login screen it freeze on a screen similar to the "Ubuntu" one and just hangs out there. What can I do to fix this?

---

### Post by Pragmatist on 2006-08-27
> **Alex6969 said:**
> Ok so yesterday i was messing around with xsession. well now when i try and boot ubuntu it loads everything like normal (where it says "Ubuntu" and has the progress bar) it finishes loading everything, but then when it sapposed to go to the login screen it freeze on a screen similar to the "Ubuntu" one and just hangs out there. What can I do to fix this?

Use a liveCD like Ubuntu's or Knoppix to access the config files (xsession) and see if you can fix what you did (you did backup the original file before messing with it, right? :)  Here are the steps I'd try:

1.) If I backed up xsessions, just replace with backup copy.

2.) If not backed up, search the system for a default xsession file (or even google for it if need be).

3.) Reinstall X and GDM

---

