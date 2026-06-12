---
title: "[SOLVED] Volume levels on Ubuntu"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Bunky on 2007-11-07
Is it normal for the volume on Ubuntu (I have Feisty Fawn at present) to be lower than Windows? It's not so low it's problematic but it's certainly quieter. Is there anything I can tweak to get it louder?

 :guitar:

Cheers.

---

### Post by Inxsible on 2007-11-07
type in ```
alsa-mixer
``` in a terminal (or is it alsamixer -- blast !! i can't remember) and make sure all of the volume levels are at max.

---

### Post by Bunky on 2007-11-07
> **Inxsible said:**
> type in ```
alsa-mixer
``` in a terminal (or is it alsamixer -- blast !! i can't remember) and make sure all of the volume levels are at max.

I love this forum. Thank you. Much better. :)

It worked with "alsamixer -- blast" btw.

---

### Post by Inxsible on 2007-11-07
> **Bunky said:**
> I love this forum. Thank you. Much better. :)

It worked with "alsamixer -- blast" btw.
Really ???

The blast was not part of the command. I was just cussing !

it should just be```
alsamixer
```But I see how that "blast" could have been confused with regards to this, since  many sound cards have sound blasters.

Anyway, My bad !!

---

### Post by Bunky on 2007-11-07
> **Inxsible said:**
> Really ???

The blast was not part of the command. I was just cussing !

it should just be```
alsamixer
```But I see how that "blast" could have been confused with regards to this, since  many sound cards have sound blasters.

Anyway, My bad !!

haha!! Well it worked with the cursing. Although it works without the cursing too. :)

---

