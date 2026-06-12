---
title: "X is spewing out a &quot;mesh of textured color&quot;."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Starks on 2007-03-09
Upon boot up, after the all the info displays, I am treated to a screen of crazy color at what would be the Ubuntu login screen. I know this because if I blindly enter my login and password, I hear the login music. Even if I log in, the crazy colors remain.

How do I fix this?

---

### Post by igknighted on 2007-03-09
What type of graphics adaptor do you have, and have you installed the drivers for it?

---

### Post by Starks on 2007-03-09
Intel GMA950. I have the i810-modesetting driver installed.

Would uninstalling it through terminal and reinstalling the regular i810 do me any good?

---

### Post by Starks on 2007-03-09
At any rate, are psychedelic screens like this common? Cuz the colors and patterns look totally random.

---

### Post by igknighted on 2007-03-09
> **Starks said:**
> At any rate, are psychedelic screens like this common? Cuz the colors and patterns look totally random.

Not really, usually if something goes wrong the screen is just black or X crashes.  Any particular reason you are using the modestting driver?  If not try the standard one.

---

### Post by Starks on 2007-03-09
> **igknighted said:**
> Not really, usually if something goes wrong the screen is just black or X crashes.  Any particular reason you are using the modestting driver?  If not try the standard one.

Okay. How do I uninstall the modsetting driver and install the regular one using terminal?

---

### Post by igknighted on 2007-03-09
look for it synaptic (search i810) and remove the one you dont want and install the one you do.

---

### Post by Starks on 2007-03-09
> **igknighted said:**
> look for it synaptic (search i810) and remove the one you dont want and install the one you do.

The X server doesn't display any useful. I need to do this through terminal or recovery mode.

---

### Post by jordanmthomas on 2007-03-09
Since he doesn't have X, he'd probably want to use apt-cache search
ie
```
apt-cache search i810
```

---

### Post by igknighted on 2007-03-09
thank you, good catch.  "aptitude search i810" works as well

---

### Post by Starks on 2007-03-09
(still typing from XP)

Okay, so what do I do after entering that command?

Also, what is the difference between apt and aptitude?

---

### Post by Starks on 2007-03-09
I figured out the first part, X is working fine now...

But what was the difference between the two commands? Are aptitude and apt the same?

---

### Post by jordanmthomas on 2007-03-09
Aptitude is just kind of a buffed up apt.  The main difference is the way they handle dependencies.  For example, if you install a program with apt-get it will grab the dependencies and install them.  So will aptitude.  The difference comes when uninstalling or when there is a dependency problem.  When uninstalling a program aptitude will also uninstall anything that was installed as a dependency but isn't needed by any other programs, while apt will just leave the useless package.  

If there is some sort of conflict aptitude will offer suggestions for solutions, whlie apt doesn't.
Hope this helps.

---

