---
title: "Flash in Firefox using wrong sound card"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by tac-tics on 2006-12-16
Hello. I'm having issues with Firefox. I spent a good two hours trying to get my Flash plugin to make noise. Finally, I realized that Firefox was simply sending the sound to the wrong soundcard. I have two soundcards, one an Audiophile2496, the other, a generic built-in card.

I want to use my Audiophile. Rhythmbox plays my music through it, but Firefox goes through the internal card. Can someone explain how I can change which card Firefox sends sound to?

Thanks.

---

### Post by xyz on 2006-12-16
Hi tac-tics,

From the Ubuntu Guide:
In a terminal, copy/paste
```
sudo asoundconf list
```
You'll get something else; this is what I get:
> Names of available sound cards:
I82801DBICH4

and...
```
sudo asoundconf set-default-card example
```
Type in the soundcard you want instead of 'example'.

---

### Post by Bachstelze on 2006-12-16
I'd recommend you disable your builtin card in your BIOS if you don't use it, to avoid confusions.

---

### Post by tac-tics on 2006-12-16
I have disabled the card in my BIOS and I set the default card, but it didn't work.

---

### Post by xyz on 2006-12-17
Could the problem be else where then?

---

### Post by tac-tics on 2006-12-24
Does anyone else have any advice?

---

