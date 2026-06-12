---
title: "Compiz bug in feisty?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-04-21
Some times I see white streaks whenever I use Compiz in Feisty. I used to use Beryl and this wouldn't happen, however I love Compiz's speed. Is there a configuration manager for compiz? How can I get rid of the white streaks.

---

### Post by Rospo Zoppo on 2007-04-21
If you do ```
sudo apt-get install gnome-compiz-manager
``` you will have the preference GLDesktop :)

---

### Post by DreamcastJack on 2007-04-21
you know I used the 3D desktop cube once and it worked..restarted and never worked again, wobbly still works..but oh well, if its easy to fix i'd like to know..if not I wont lose sleep over it (not a huge 3D desktop fan)

---

### Post by Rospo Zoppo on 2007-04-21
> **DreamcastJack said:**
> you know I used the 3D desktop cube once and it worked..restarted and never worked again, wobbly still works..but oh well, if its easy to fix i'd like to know..if not I wont lose sleep over it (not a huge 3D desktop fan)

Graphic card?

---

### Post by DreamcastJack on 2007-04-21
> **Rospo Zoppo said:**
> If you do ```
sudo apt-get install gnome-compiz-manager
``` you will have the preference GLDesktop :)

okay, well that fixed mine too..lol thanks.

---

### Post by Rospo Zoppo on 2007-04-21
> **DreamcastJack said:**
> okay, well that fixed mine too..lol thanks.

Np ;)

---

### Post by Fillibuster on 2007-04-21
Compiz is working fine for me (cube and wobbly and water) but I want the extra plugins like animation, and 3-d.  When I try sudo apt-get install compiz-extra it says that there's no such thing.  What repo should I be using?  Or is there another issue?  This is really kind of irritating because I used to use Beryl on Edgy and it worked like a charm, but when I try installing Beryl on Feisty it doesn't work at all so I kind of have to stick with Compiz...I just really want those extras!

---

### Post by Rospo Zoppo on 2007-04-21
> **Fillibuster said:**
> Compiz is working fine for me (cube and wobbly and water) but I want the extra plugins like animation, and 3-d.  When I try sudo apt-get install compiz-extra it says that there's no such thing.  What repo should I be using?  Or is there another issue?  This is really kind of irritating because I used to use Beryl on Edgy and it worked like a charm, but when I try installing Beryl on Feisty it doesn't work at all so I kind of have to stick with Compiz...I just really want those extras!

Maybe ```
sudo apt-get install compiz-freedesktop-extra
sudo apt-get install gnome-compiz-manager-extra
```

---

### Post by Fillibuster on 2007-04-21
^Tried both and it can't find either package

---

### Post by orb9220 on 2007-04-21
Do you have all the needed repostories enabled?

synaptic then check Universe and multiverse is checked,

---

### Post by syalam on 2007-04-22
how can I get the compiz-extra stuff? I downloaded it from Synaptic but I don't know where I can enable the extra effects..i have GLDesktop

---

### Post by Cerb on 2007-04-24
same here :(

---

