---
title: "Nautilus slow all of the sudden."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by buckwheat12n on 2007-06-11
I have a relatively new install of feisty running on my PC.  Today I noticed when opening up my Music folder that it takes almost a minute or longer to open the folder up.  This folder always opened up almost instantly before.  Any ideas as to what may be causing this?  I have ran the top command in terminal and it shows Nautilus using 90% of my CPU.

---

### Post by starcraft.man on 2007-06-11
> **buckwheat12n said:**
> I have a relatively new install of feisty running on my PC.  Today I noticed when opening up my Music folder that it takes almost a minute or longer to open the folder up.  This folder always opened up almost instantly before.  Any ideas as to what may be causing this?  I have ran the top command in terminal and it shows Nautilus using 90% of my CPU.

Ok, that is very weird. How many files/folders do you have in music, like a few hundred GBs? Short of that, I don't see any real reason why it would take so long. Maybe bumping your post will get someone's attention with the answer.

---

### Post by cwmoser on 2007-06-11
I had trouble with Nautilus running slowly when accessing an NTFS partition.
The screen would dim and then come back several times until the folder contents was displayed.  This was especially true when I tried to access my C-drive windows XP partition.  But, when I went to the command prompt, I could cd down into the NTFS directory structure and the response was quick.

Then, I cloned my Ubuntu partition to another partition and instantly Nautilus works quickly with everything including NTFS partitions.

Carl

---

### Post by buckwheat12n on 2007-06-14
OK, I've narrowed the problem down to list view.  If I switch to icon view the files appear within 5 seconds or so, if I go to list view it takes 2-3 minutes for the files to appear when opening a folder that has roughly 2000 mp3's in it.  Is there anyway to speed Nautilus up, or is it just this slow my nature?  I also might add that I did re-install Ubuntu and it's still doing it.

---

### Post by Vogateer on 2007-09-22
I noticed a dramatic drop in speed when I tried a different icon set and theme. This obviously might not be the problem for you, but made a seriously noticeable difference for me, speeding things up by a factor of 5 at least when I switched back to Human.

---

### Post by useResa on 2007-09-23
I am experiencing the same, since last Friday (Sep 21, 2007) starting my Feisty install takes minutes!! Also the "square in the center" when starting up stays there for minutes, displaying the word "Nautilus".

I have changed nothing myself since last Friday and before this day it started in seconds. Anyway I can do sort of scan what it is doing during this period?

---

### Post by Tomàs M. on 2007-10-27
> **buckwheat12n said:**
> OK, I've narrowed the problem down to list view.  If I switch to icon view the files appear within 5 seconds or so, if I go to list view it takes 2-3 minutes for the files to appear when opening a folder that has roughly 2000 mp3's in it.  Is there anyway to speed Nautilus up, or is it just this slow my nature?  I also might add that I did re-install Ubuntu and it's still doing it.
Same problem here after a Gutsy upgrade, only with list view and with "default ampliation level" at 50% in preferences...

---

### Post by Tomàs M. on 2007-10-30
x

---

### Post by handaxe on 2007-11-01
Something I found re nautilus: I suggest seeing if you have assistive technology enabled and if so disable it, reboot.
 "preferences" -> "Universal Acess" -> etc. (under Gutsy)
 This one can kill the nautilus experience :-)

HA

---

### Post by ceefour on 2008-04-14
> **buckwheat12n said:**
> I have a relatively new install of feisty running on my PC.  Today I noticed when opening up my Music folder that it takes almost a minute or longer to open the folder up.  This folder always opened up almost instantly before.  Any ideas as to what may be causing this?  I have ran the top command in terminal and it shows Nautilus using 90% of my CPU.

Go to Nautilus Preferences, and on List View Columns use only default columns and REMOVE "Size" column. This makes things much faster especially on network share browsing.

---

