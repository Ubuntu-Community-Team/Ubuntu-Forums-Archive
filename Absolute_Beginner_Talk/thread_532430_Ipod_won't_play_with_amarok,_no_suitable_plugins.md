---
title: "Ipod won't play with amarok, no suitable plugins?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-08-22
I'm trying to configure my moms ipod to work on her new ubuntu computer (yay, another new recruit!:KS)

I've got amarok to open when the ipod is attached, and i've gotten it to read the songs... but it cannot play any songs on the ipod... i was wondering if there is some sort of codec or something that would allow me to do that...


also, i can't seem to log on to the ubuntu forums on her computer (or any other computer for that matter) it logs on for a second, and then goes back to  *no user name or password*

---

### Post by Clay_Banger on 2007-08-22
for playing in amarok, make sure you have these packages installed:
amarok-xine
libxine-extracodecs
libxine1

if u do... i dont know.

---

### Post by Hobo Joe on 2007-08-22
How did you set up the iPod?

---

### Post by Arthur Archnix on 2007-08-22
What's the file extension of the music? *****.ogg will transfer to the ipod, but never be able to be played unless you replace the ipod software, which is also impossible on some models.

---

### Post by Tyke91 on 2007-08-22
alright, i figured it out


to set up the ipod, just play around in the amarok configuration menu

to play the ipod format songs, enable universal repositories, then play one of the songs through totem... it will automatically download all required codecs :)

---

