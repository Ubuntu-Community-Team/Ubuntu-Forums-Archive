---
title: "es1988 allegro-1 not working"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by StackError on 2006-03-20
Hello:
after applying the ubuntu updates and rebooting my ess1988 allegro-1 sound card stopped working....I found a post froma user that has the same laptop as me and he disabled his modem and his sound card worked.... i tried that and it did work for me
This is my first stab at using linux and except the s/card issue it is much better than i expected!
any help would be highly appreciated!!

Thankx in advance

S.

---

### Post by StackError on 2006-03-20
Well i figured it out from reading the other sound card issues....
it seems that afrer the updates my sound was disabled somehow.
what did was: sudo lspic -v | grep audio and my sound card was detected....
then i did: sudo alsamixer and then toggeled thru till i saw that the master was turned down.... i brought the sound up and then tested...... and now my sound is working.... my only question now is:
where can i download some better sounds at????

this forum is full of information i have never seen in any other linux disrto help forum before.... I am glad i decited to try Ubantu!!!!!!!
Thankx for all of the valuable information!!!

:mrgreen: 
S

---

