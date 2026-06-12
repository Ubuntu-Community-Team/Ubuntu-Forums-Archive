---
title: "mic not working..."
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by kennster on 2008-02-13
i have a ASUS M2N-SLI Deluxe Socket AM2 MOBO and i cant get the mic to work the cases has a front mount mic port as whell that used to work with a lotta work on vista... any one know how i could get it working..?

---

### Post by OffAxis on 2008-02-13
does the mic port on the back of the case work?

---

### Post by kennster on 2008-02-13
> **OffAxis said:**
> does the mic port on the back of the case work?

i think it did at one point... cant member if i ever got it to but i used to have the front port working ... i dont care witch one i get working as long as 1 of them dose

---

### Post by OffAxis on 2008-02-13
The front port may not be connected properly, so you should work off the back one for the time being because you know it's doable.

try 
```
aplay -l
```

This should list your detected sound cards.

Then try
```
alsamixer
```

If you've got more than one soundcard installed, make sure that the 'Card' specified in the upper left hand corner is the correct one. 
Use Tab to move across the Views (Playback, Capture, All) and arrow keys to move across the options. Tab over to the Capture View and arrow key over to the mic or Capture and give it some juice (up arrow).
Escape to quit.

---

### Post by kennster on 2008-02-14
> **OffAxis said:**
> The front port may not be connected properly, so you should work off the back one for the time being because you know it's doable.

try 
```
aplay -l
```

This should list your detected sound cards.

Then try
```
alsamixer
```

If you've got more than one soundcard installed, make sure that the 'Card' specified in the upper left hand corner is the correct one. 
Use Tab to move across the Views (Playback, Capture, All) and arrow keys to move across the options. Tab over to the Capture View and arrow key over to the mic or Capture and give it some juice (up arrow).
Escape to quit.

nothing... :(

---

