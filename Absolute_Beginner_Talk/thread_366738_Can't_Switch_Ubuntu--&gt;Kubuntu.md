---
title: "Can't Switch Ubuntu--&gt;Kubuntu"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-02-21
So I did:
```
sudo apt-get install kubuntu-desktop
```
which went fine but when I log out or reboot & try to change session to KDE, it isn't there to be chosen!
Any ideas why this might be so? (FYI:  Edgy on laptop Dell6400 core2Duo)

---

### Post by taurus on 2007-02-21
There is no option for KDE in the Sessions at the bottom left corner?

---

### Post by flyingsolo on 2007-02-21
Exactly!  I was quite surprised because everyone says it's such an easy process.
At log in, I have the following choices:

Select Language
Select Session
Remote Login via XDMCP
Restart, Shutdown, Suspend, Hibernate

under Select Session, I get:
Last session
Default Session
GNOME
Failsafe Gnome
Failsafe Terminal

---

### Post by taurus on 2007-02-21
Try

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by flyingsolo on 2007-02-21
Thanks Taurus!  Now I'm in Kubuntu!

...but still, a question arises, why didn't this work the first time?  What did the update do that made the 2nd install work?  ie-what was I missing on the first go around?

---

### Post by skyhopper88 on 2007-02-21
I believe it was because you used apt-get. Aptitude is better with package dependancies.

---

