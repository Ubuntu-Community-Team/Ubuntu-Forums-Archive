---
title: "New User Here!"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Bo.. on 2008-04-12
Hello.
I'm a new user of Ubuntu (Gutsy Gibbon) and i'm having a bit of trouble.

I'm trying to play a DVD on here, but it is asking me to install a plug-in.
Ok, that seems easy, but whenever i try to check the box, it just keeps refreshes the available plug-ins for DVDs to work

I need help :confused:

---

### Post by Gulyan on 2008-04-12
did you try to select one of those plugins? :lolflag:

---

### Post by joshrobinson on 2008-04-12
> **Gulyan said:**
> did you try to select one of those plugins? :lolflag:

that probably wont work, considering libdvdcss2 isnt in the ubuntu repo's due to legal issues

to the OP, run these commands in a terminal
applications > accessories > terminal

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

```
sudo apt-get install libdvdcss2

```

will it play a dvd now?

---

### Post by Bo.. on 2008-04-12
It let me download the plugin but then it said this

"Cannot install 'gstreamer0.10-plugins-ugly"
"This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first. Switch to the 'synaptic' package manager to resolve this issue"

I'm stuck. :(

---

### Post by zvacet on 2008-04-12
Check that you have all repositories open.System>admin>software sources>check all boxes under Ubuntu software and under updates tab.Reload.Go to the synaptic and uninstall** libdvdcss2**.Type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

When you are finish with that go to the synaptic and install libdvdcss2 again.

---

