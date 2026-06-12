---
title: "[SOLVED] I broke my Compiz Fusion lol..."
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Spoken on 2008-02-08
I was having numerous problems with my effects and what not, so i when to synaptic and removed my compiz fusion, and after i reinstalled it, i still couldnt get anything to work, when i go to system > preference > appearance and go to visual effects, when i change it from none to anything else, it says "visual effects could not be enabled"

i want to get my compiz fusion, emerald, and awn dock navigator working again.  What do i need to do.

---

### Post by ispy on 2008-02-08
type 
```
compiz --replace
```

If that doesn't work, reboot. that has solved many of my compiz woes.

---

### Post by nynoah on 2008-02-08
true that on the reboot

---

### Post by Spoken on 2008-02-08
I have rebooted and used "compiz - replace" , neither worked, and everything i said above still stands

when i used the command i got this error.

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by ispy on 2008-02-08
your screwed man, your Video card is blacklisted by compiz. you can go around it, but it might cause instabilities and such. 

read this forum:
[HTML]http://ubuntuforums.org/showthread.php?t=582112[/HTML]

sorry man, that's all you can do it looks like.

---

### Post by Spoken on 2008-02-08
hmm, what i dont understand is that everything was working fine , until recently, and couple things messed up, then some more. :l

---

### Post by Spoken on 2008-02-08
kk well thank you both, ive got my effects back up, and now i know im blacklisted lol. its ok, i will find ways to work around it :P

---

### Post by ispy on 2008-02-08
...

---

