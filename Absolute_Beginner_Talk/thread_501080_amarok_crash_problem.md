---
title: "amarok crash problem"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by mrsempai on 2007-07-14
ok, heres my problem... i changed my music folder and now amarok crashes... i tried uninstaling it with apt-get remove and synaptic and instaling it again but somehow the "where is the music" settings stay the same... (my music is in a ntfs partition mounted with ntfs-config and i use ubuntu 7.04)

any ideas on how i can solve this??

thanks in advance :)

---

### Post by ev5unleash1 on 2007-07-14
Some programs like Audio and Video Players tend to crash if Compiz, Desktop Effects or Beryl is running. If so turn that off. That's all I can provide with the question.

---

### Post by BoneSaw on 2007-07-14
if you want to completely remove amarok you need to

sudo apt-get remove --purge amarok

or go into synaptic and mark it to completely remove.

---

