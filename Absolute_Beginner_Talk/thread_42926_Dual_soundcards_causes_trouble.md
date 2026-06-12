---
title: "Dual soundcards causes trouble"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-20
Hey, after swindling through the jungle of Linux distrubutions I finally found one that I think I like, so I ended up here. *greets oneself welcome to the forum*

So far I've only had one problem. My computer uses dual soundcards, one of them is intergrated to the motherboard, and one was bought separetly. The intergrated one is a Intel-something, since it's an Intel-based motherboard, and the one I uppgraded to is a Creative SoundBlaster Live! 5.1 (you might have heard of it ;)).

Now, I've figured out that the sound is not comming through my speakers because Ubuntu choose to use my intergrated soundcard (wich I found kinda weird since my BIOS is set to SB Live).

How do I set SBL as deafult? It would seem some applications use their own settings, so I guess I have to go ahead and fix those manually, but I want all new installed applications to use SBL. And for future referense I'd like to know how to make the next install choose SBL instead of my integrated card.

//Trojan1313

---

### Post by diebels on 2005-06-20
this will be more simple in breesy, but for hoary you must blacklist the module for the integrated card.
Run lsmod | grep snd to get the name of the module. And add it to /etc/hotplug/blacklist

---

### Post by Trojan1313 on 2005-06-20
[QUOTE=diebels]this will be more simple in breesy, but for hoary you must blacklist the module for the integrated card.
Run lsmod | grep snd to get the name of the module. And add it to /etc/hotplug/blacklist[/QUOTE]
EDIT: Okay, I think I found the thingie when I did the lsmod, but blacklist is protected, how do I unprotect it?


So I open the terminal and first input "lsmod", then "grep snd". How do I add it to /etc/hotplug/blacklist? Just browse to there?
Did I get it all right?

ls is a list-command, right? And mod means module. What exactly is a module? Is it like a built-in driver or something?
Thanks for taking your time answering all my stupid questions. :)

And what's breesy?

---

### Post by TristanMike on 2005-06-20
Breezy is the next Ubuntu release

---

### Post by diebels on 2005-06-20
Hold in the [ALT] key, and press the [F2] key. Enter "gksudo gedit" in the run command window that pops up. Now you can edit all protected files.

---

