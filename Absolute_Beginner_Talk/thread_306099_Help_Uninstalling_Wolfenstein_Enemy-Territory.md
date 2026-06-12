---
title: "Help Uninstalling Wolfenstein Enemy-Territory"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Phalangees on 2006-11-24
I would like to uninstall Wolfenstein Enemy Territory but I don't know how. I tried going through Synaptic and through add/remove but it can't find it. I can't go through Places->Computer->usr->local->games and delete the directory because it tells me I don't have permission. I tried the rm command in the terminal but It says that it's a directory and not a file. Any help would be great. Thanks

---

### Post by TheRingmaster on 2006-11-24
how did you install it to begin with?

---

### Post by kinematic on 2006-11-24
try > sudo rm -rf /urs/local/games/enemy territory
and also remove the symlink in /usr/local/bin.
then goto /home/Phalangees.....select show hidden files and remove the folder called .etwolf and it's removed :wink:

---

### Post by Phalangees on 2006-11-24
Ah ha ha thanks a bunch. That's great. I installed it using the sh command on the run file and it had a whole nice text based install but no uninstall.

THANK YOU!!

---

### Post by kinematic on 2006-11-24
you're welcome ;)

---

