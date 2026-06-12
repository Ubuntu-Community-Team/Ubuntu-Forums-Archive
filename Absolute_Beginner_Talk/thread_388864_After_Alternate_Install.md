---
title: "After Alternate Install"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-03-20
So I've installed ubuntu with the alternate install disc since the normal one wasnt working for me.  But now when I boot up into ubuntu all I get is a command line prompt, I can sign in just fine but I dont know where to go from there.  Is there any way to get from here to a normal ubuntu desktop?  And from there can I install normal ubuntu so it always shows up as the graphical desktop?

---

### Post by zvacet on 2007-03-20
ctrl+alt+F1
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by mcduck on 2007-03-20
What install option did you use? The alternate CD should install exactly same Ubuntu, with Gnome desktop, that the Live CD installs..

Anyway, you could try running 'sudo apt-get update && sudo apt-get install ubuntu-desktop'. If your network connection is working that should install the desktop for you.

---

### Post by justleen on 2007-03-20
i recon you installed a command line system. Try the suggestion of the poster above to install the graphical system...

---

### Post by unisol on 2007-03-20
typing startx should get you into graphical mode if ubuntu desktop is installed.

---

### Post by zvacet on 2007-03-20
If you installed non graphical version here is how you can get desktop
```
sudo apt-cdrom add
```
```
sudo aptitude install ubuntu-desktop
```
No need for net

---

