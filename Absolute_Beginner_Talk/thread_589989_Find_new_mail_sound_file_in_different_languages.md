---
title: "Find new mail sound file in different languages"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by sergiodlc on 2007-10-24
Hi:

I would like to configure the mail-notification package to play a sound file uppon new mail arrivals. It can execute a command when new mail arrives and I guess this is what I have to set. I have to questions:[LIST=1]
[*]What command can I use to play a sound file?
[*]Where can I download sound files suitable for mail arrival notifications in languages other than English (I'm a native Spanish speaker)?
[/LIST]

Thanks in advance,

Sergio

---

### Post by luisromangz on 2007-10-24
Instead of using sound files, you might try to make your computer speak using festival.

There are spanish voices for festival in the Ubutu repositories, but I prefer the voices that are being developed for Guadalinex. You can look for them in google.

A command for festival would be:

echo "hola" | festival --tts

---

### Post by sergiodlc on 2007-10-24
> **luisromangz said:**
> Instead of using sound files, you might try to make your computer speak using festival.

There are spanish voices for festival in the Ubutu repositories, but I prefer the voices that are being developed for Guadalinex. You can look for them in google.

A command for festival would be:

echo "hola" | festival --tts

Thanks a lot, I'm installing the whole stuff.

---

### Post by sergiodlc on 2007-10-24
OK, I have installed and tested festival and the Guadalinex voices but they are ugly, man. Maybe a simple wav file for new mail is better

---

