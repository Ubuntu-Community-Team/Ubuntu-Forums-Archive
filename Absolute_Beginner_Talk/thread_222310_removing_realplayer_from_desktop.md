---
title: "removing realplayer from desktop"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by gra1 on 2006-07-24
When installing realplayer I acidently installed it as root to my desktop and now can't remove it, any ideas  how i can can get rid of it.

Thanks

---

### Post by GuitarHero on 2006-07-24
You could try gksudo nautlius, then navigate to the folder and delete it.

---

### Post by trivialpackets on 2006-07-24
I think sudo rm realplay.desktop (orwhatever it is called would work as well) from the terminal.

or

sudo rm ~/Desktop/realplay.whatever

would probably be better so you don't have to get to the Desktop.

---

### Post by gra1 on 2006-07-25
I tried  the following  in side a terminal and got the following message

graham@graham:~$ sudo rm ~/Desktop/RealPlayer/
rm: cannot remove `/home/graham/Desktop/RealPlayer/': Is a directory

---

### Post by DaleFarrell on 2007-11-28
Did you remove it? I want to move mine to anywhere but the desktop, but it tells me I am "not the owner". So, can someone tell me how to move it, and where would one put an app like this? thanks.

---

### Post by philinux on 2007-11-28
Best bet is to go to synaptic and remove it.

Then reinstall it correctly.

---

