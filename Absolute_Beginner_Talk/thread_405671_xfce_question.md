---
title: "xfce question"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-04-10
I have a Dell 700m, 512MB RAM 1.6ghz processor, and I'm running GNOME right now its running fine, but I heard I can get better perf if I switch to XFCE. Is there a huge difference between the two? How can I install xfce to test it out? Also will I be able to switch between XFCE and GNOME?

---

### Post by heimo on 2007-04-10
That's a great question. Go to synaptic package manager, or use your favourite command line program to install xubuntu-desktop. Or to test KDE, install kubuntu-desktop. You'll probably need couple hundred megabytes of hard disk space to do that.

```
sudo aptitude install xubuntu-desktop
```Then logout, and on the logon screen, change session to xfce or kde and log in as usual. You can make the change permanent, or change to each session. Experiment. See yourself which one you like best.

---

### Post by Kobalt on 2007-04-10
XFCE is a bit more responsive than Gnome, it's true. 
To install it and test it, open a Terminal and enter ```
sudo aptitude install xubuntu-desktop
```
When it's done, you'll be able to chose between a Gnome session or a XFCE one at the login screen, under Options > select session.
You can remove it later on if you want with ```
sudo aptitude remove xubuntu-desktop
```

---

