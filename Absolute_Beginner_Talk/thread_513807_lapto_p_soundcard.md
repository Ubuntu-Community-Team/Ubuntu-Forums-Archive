---
title: "lapto p soundcard"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by duncancan on 2007-07-30
Hi Everybody,

My laptop -- a Dell Inspiron 9300 -- has an onboard sigmatel c-major soundcard (for which i believe the system's loading the snd-intel8x0 module), but i don't want to use that one. i want to use my indigo IO soundcard (alsa module snd-indigoio) instead.

I'm guessing this is fairly easy to accomplish, but i don't know how.

Thanks,
Duncan

---

### Post by sunshine12 on 2007-07-31
May be try this...

```
asoundconf list
asoundconf set-default-card YOUR_CARD_NAME
```

first command show you list of the installed soundcards.
and replace YOUR_CARD_NAME with the card you want to chose.

do it in gnome-terminal... (Applications--accessories--terminal)

post if  any problem..

---

### Post by duncancan on 2007-07-31
Hi Sunshine. I think I may have done it the long way, but it worked:

I more or less followed the instructions [here]("http://geocities.com/rburra/echo.html"), and it all works.

Sorry to've wasted your time! [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

-Duncan

---

