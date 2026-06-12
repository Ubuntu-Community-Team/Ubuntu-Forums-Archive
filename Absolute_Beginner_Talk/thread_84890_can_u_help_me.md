---
title: "can u help me"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by tulliohermil on 2005-11-01
hi, i'm Tullio.I've install linux ubuntu on my pc.I want to install the gcc complator, but i dont know how can I.
I am a novice: so I hope it will be so easy.
if someone can help me and describe me how to do I'll be eternaly gratefull to him.
thank you very much.sorry for my bad english.
tullio:|

---

### Post by Pathogenix on 2005-11-01
As far as I know, the GCC compiler will be automagically installed as part of a basic install.

If not, the system menu > administration > synaptic and search for gcc.

Um... if I've forgotten the menu structure, and there is no system menu, open a terminal and type ```
 sudo apt-get install build-essential 
```
and enter your password when prompted.

Just a hint, when posting messages, you'll get better responses if you have a useful subject. "How do I install GCC" is likely to get more attention than "Can u help me"

Welcome to Ubuntu, anyway :)

---

### Post by MrCheese on 2005-11-01
Run Synaptic (in Administration section 0f Gnome menu) using your user password when prompted. Search for gcc and select the version you want, Apply changes and the package will either prompt for the cd (if available from their) or download & install if you have an internet connection active.

Synaptic can be used to install & manage all the packages available to Ubuntu users - check [www.ubuntuguide.org](www.ubuntuguide.org) for many useful help articles

---

### Post by lorenco on 2005-11-01
You can alway try aptitude ( a text base package manager) from the command line

---

### Post by tulliohermil on 2005-11-01
tank you very much for your disponibilities and advices.

---

