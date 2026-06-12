---
title: "Frostwire/Limewire Won't Open"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by DrTsus on 2007-07-01
I have Feisty Fawn and Compiz-Fusion and now neither Limewire nor Frostwire will run. I open them, and the dialogue with the tip opens but the box is white! Yesterday Frostwire ran fine, but now it doesn't! PLEASE HELP.

---

### Post by Raineer on 2007-07-01
Limewire is known to be incredibly picky about the Java version. I had this and ended up using Java 1.4 instead of "5" or "6". 1.4 worked fine.

For some reason, last week I had to switch to 1.5 for another program and Limewire still worked fine.  Quite a known bug but Limewire blames it on Java and has no intention of fixing.

---

### Post by qamelian on 2007-07-01
You can fix this problem by downloading and installing the latest version of the Java Runtime Environment from [http://java.sun.com](http://java.sun.com). Once it's installed, you need to run:
```
sudo update-alternatives --config java
``` in a terminal to make the new version of java the default.

---

### Post by Raineer on 2007-07-01
For what it's worth, that's how I got the problem. Neither 1.6 or 1.5 would work, I had to go back tot he 1.4 JRE.

---

### Post by ThrobbingBrain66 on 2007-07-01
[http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java)

The above link will allow you to use Java/Swing apps (Frostwire, etc) with Beryl/Compiz.  It looks complicated but it works nicely.

---

### Post by qamelian on 2007-07-01
> **Raineer said:**
> For what it's worth, that's how I got the problem. Neither 1.6 or 1.5 would work, I had to go back tot he 1.4 JRE.

This is a known bug in 1.5 and 1.6. Upgrading to 1.6 update 1 does fix the problem. This is a bugfix to Sun's original 1.6 release.

---

### Post by Raineer on 2007-07-01
> **qamelian said:**
> This is a known bug in 1.5 and 1.6. Upgrading to 1.6 update 1 does fix the problem. This is a bugfix to Sun's original 1.6 release.

Oh, cool! Thanks for the tip :D

---

