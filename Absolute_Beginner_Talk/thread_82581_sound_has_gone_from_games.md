---
title: "sound has gone from games"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-10-26
i have had a few good wins with ubuntu nearly all my early problems are fixed, now i have a new one.
the sound is missing from games like frozen bubble and battleships etc. It works fine in everything else ,system sounds are fine, can play music ok. my sound card is an inbuilt one ubuntu lists it as a realtek alc655 rev o.
in frozen bubble it does not allow me to tick the sound box.

any ideas

---

### Post by acorrigan on 2005-10-29
kill the esd process (ps -A    to find the id #)
then when the game starts sound should be enabled (fixed it for me)

do a search on the forums for more details, this was discussed in numerous threads

---

### Post by PatrickMay16 on 2005-10-29
[QUOTE=acorrigan]kill the esd process (ps -A    to find the id #)
then when the game starts sound should be enabled (fixed it for me)
[/QUOTE]
An easier way to do this is just to type "killall esd". Then once you've finished playing the game and would like esd back so programs like totem can work again, just type in a terminal "esd".

---

