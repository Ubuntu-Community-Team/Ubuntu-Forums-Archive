---
title: "Ess Audio Drive Help Please!!"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-07-25
im am having trouble with my sound card which is ESS audio drive. I cant hear any sound at all. ive just installed the new ubuntu 6 and i need help on how to work my sound card... please help!!

---

### Post by pistcivet on 2006-07-25
To get my old sound card to work, I added this line:
snd-es18xx
to /etc/modules.

Look in ~/Examples for book-toc.html, click Support and Typical Problems,
find the section "Ubuntu Has Not Detected My Old Sound Card" for more help.

(I'm assuming you have an ancient ISA sound card - similar to mine)

---

### Post by rck_hitokiri on 2006-07-25
yeah i have an ancient soundcard.... i tried /etc/modules but it says "permission denied" what am i gonna do? thx

---

