---
title: "But, where's my installed program?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by Maverick-ZA on 2005-12-23
I've installed an update( p7zip) but cannpt access it. What have I done wrong. Must one put it in the menu manually? (Can you see I'm from the M*******t era?):confused:

---

### Post by bscbrit on 2005-12-23
Where have you installed this update from?  And how did you do it - synaptic, apt-get?

---

### Post by Maverick-ZA on 2005-12-23
Hi bscbrit! I updated the package from the package manager, then proceeded to use synaptic to install. All went well, but can't unzip with it or see it in the apps, or 'open with' ? Thanks:)

---

### Post by bscbrit on 2005-12-23
Some useful command-line commands for you to use:

whereis p7zip  - will tell you where it has been stored

whatis p7zip  - will tell you what it does.

When you know where it is, you can use it from the commandline e.g.

/usr/bin/p7zip   (IF that is where you find it)

Typing 'man p7zip' or 'info p7zip' will tell you more about _how_ to use it.

To put it into your menu system, run 'smeg' - which you might need to download using synaptic initially.

smeg is the same as Applications -> System Tools -> Applications Menu Editor (or it looks the same on my system!)

---

### Post by Madpilot on 2005-12-23
[QUOTE=bscbrit]To put it into your menu system, run 'smeg' - which you might need to download using synaptic initially.

smeg is the same as Applications -> System Tools -> Applications Menu Editor (or it looks the same on my system!)[/QUOTE]

Menu editing is included in Breezy by default, you don't need smeg for basic edits.

Thanks for whereis and whatis, btw, I hadn't known about those CLI tools!

---

