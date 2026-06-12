---
title: "How to get Compiz to start at startup"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-07-05
Well, I've searched the forums, and I just can't seem to figure this out.  I'm running Ubuntu, and have managed by some miracle to install Compiz and Emerald, and they work!  I have to start them by using alt-F2, and running compiz --replace.  How do I get Compiz and Emerald to start at system bootup?

Daniel

---

### Post by NeoLithium on 2007-07-05
Go to System -> Preferences -> Sessions and then create a new app for the session. name it what you like and in the actual command use:
```
compiz --replace -c emerald
```

---

### Post by dndrich on 2007-07-06
Hmm.  I tried this, but it did not work.  Here is what I did.  At the sessions dialog box, there are three tabs.  The first tab has to do with programs to start at startup.  I put in that code in the run section, and called it Compiz, for lack of a better name.  When I boot to Ubuntu, it doesn't start Compiz.  I just have the standard Ubuntu desktop.  What am I doing wrong?

---

