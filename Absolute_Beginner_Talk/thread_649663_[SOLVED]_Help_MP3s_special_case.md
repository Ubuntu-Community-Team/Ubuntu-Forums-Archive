---
title: "[SOLVED] Help MP3s *special case*"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by patrickaupperle on 2007-12-25
Ive been trying to play mp3s for a while now

I first tried to play mp3 by double clicking the file
it asked me if i wanted to search for a codec I said search 
it displayed 1 item
I tried to install it and got the error in the attached screen shot.

I have been surfing these forums trying stuff, but nothing worked.
Please help

---

### Post by AndyCooll on 2007-12-25
Ok, try doing as it says. Open up Synaptic (System > Administration > Synaptic Package Manager) and do a search for the "gstreamer ugly". Then try installing it.

Post back the results.

:cool:

---

### Post by Rabindranath on 2007-12-25
I had that problem long back but I dont remember how I solved it. Enable universe and multiverse in software sources, open synaptic and check the boxes "gstreamer plugins extra" and other such plugins which says gstreamer. ( ffmpeg, etc).

---

### Post by patrickaupperle on 2007-12-25
It still did not work

here is a screenshot

---

### Post by AndyCooll on 2007-12-25
And following on from the above posts, you can enable additional repositories once in Synaptic by clicking on Settings > Repositories.

:cool:

---

### Post by Rabindranath on 2007-12-25
Sorry. the gstreamer extra plugins doesn't seem to be in synaptic. Try " Add or remove Programs" It has that entry in it and I think it will include all those " ugly, bad, etc..." plugins.

---

### Post by patrickaupperle on 2007-12-25
Thank you all for the help

I found the problem

In software source the first box was not checked

I checked it 

everything works fine:KS:KS:KS:KS

---

### Post by Gaguck on 2007-12-26
hihi 
sorry i am actually having the same problem and i am not sure how to solve this yet lol
I did a search for "gstreamer ugly" but nothing showed up

---

### Post by barbedsaber on 2007-12-26
do what the fist guy did, and first guy (sorry, dont remember name.) plz mark the thread as solved, you can do this by clikcing thread tools, then mark as solved.

---

### Post by Gaguck on 2007-12-26
lol ok it works now :D
thanks.. for some reason i had to wait for a while for it to work :)

---

