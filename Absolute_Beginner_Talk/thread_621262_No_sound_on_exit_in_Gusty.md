---
title: "No sound on exit in Gusty"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-11-23
Hey, this really isn't a big issue but it would be cool to get everything working in Gusty. There is no exit sound. All I get is a pop through the speakers which occurs if the computer is muted or not. Thanks for any ideas on fixing this.

---

### Post by asmiller-ke6seh on 2007-11-23
Do you get an ENTRY sound?

---

### Post by kevindubrow on 2007-11-23
Yes I do. Thanks for helping!

---

### Post by GavinZac on 2007-11-23
im guessing the pop through the speakers is just a little surge and not related to the ubuntu software.

In system->prefs->sound, is the exit sound present?

---

### Post by kevindubrow on 2007-11-23
Yes

---

### Post by asmiller-ke6seh on 2007-11-23
I'm guessing that either the sound file is missing, or corrupted.

Try playing the sound file in whatever sound app you have, and let us know what you find.

---

### Post by kevindubrow on 2007-11-23
It plays through the sound utility and it works through the totem movie player.

---

### Post by GavinZac on 2007-11-23
> **kevindubrow said:**
> It plays through the sound utility and it works through the totem movie player.

i guess it must be a sound card issue then.

im stumped. hey, if this is your biggest issue with linux, seems pretty good to me :lolflag: wish i could help more.

---

### Post by kevindubrow on 2007-11-23
Haha exactly, but its not the only one...but I don't care enough about the others due to the lack of success I have had with fixing them. Thanks for trying though!

---

### Post by nick_h on 2007-11-23
Installing the esound package fixed this for me.

To install type:
```
sudo apt-get install esound
```

---

### Post by kevindubrow on 2007-11-23
Well something odd happens now, the first half of the sound plays and is ended by the same pop.

---

### Post by GavinZac on 2007-11-23
> **kevindubrow said:**
> Well something odd happens now, the first half of the sound plays and is ended by the same pop.

maybe install it again, you might get another little bit :D

---

### Post by kevindubrow on 2007-11-23
Haha, great idea!

---

### Post by john262 on 2007-11-23
I am getting the same thing. The exit sound starts but then it cuts off. I think that this is one of the many bugs in Gutsy. When I ran Fiesty I didn't have this problem.

---

### Post by asmiller-ke6seh on 2007-11-23
What happens if you try to use a different sound file on exit?

---

### Post by kevindubrow on 2007-11-23
I have always been confused as to how issues with Ubuntu can vary so much between different computers. No matter though, it keeps things interesting and I would still take it over Windows.

---

### Post by kevindubrow on 2007-11-23
I call shenanigans! I made the log out sound the log in sound and it decided to play the log out sound!!! It worked though...well it played through before the pop. I guess thats good enough. I would love to get rid of the pop though...it would be nice to have no sound when I am trying to use the computer quietly.

---

### Post by punkybouy on 2008-02-06
I am having the same exit sound issue after a Gutsy upgrade from Feisty.  I will try the esound thing.

---

### Post by nikoPSK on 2008-02-06
Here is your one-time fix. Go to: system -> Administration -> Login Window

goto the accessibility tab and set your preferences there. :)

---

### Post by punkybouy on 2008-02-07
Installing esound worked for me.  Thanks

---

### Post by Crumpets and Jam on 2008-02-07
I also have no exit sound. I will try esound too and report my results.

---

