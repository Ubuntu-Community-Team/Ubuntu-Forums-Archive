---
title: "[SOLVED] how do I type diacritic letters?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-02-11
How do I type diacritic letters in Ubuntu?

---

### Post by gvartser on 2008-02-11
what is "diacritic" ?

/g

---

### Post by kleo skywalker on 2008-02-11
> **gvartser said:**
> what is "diacritic" ?

/g

[http://en.wikipedia.org/wiki/Diacritic](http://en.wikipedia.org/wiki/Diacritic)

Letters with accents.

---

### Post by gvartser on 2008-02-11
Ahh oki got it thanks..

I guess it depends on what kind of keyboard layout you are using, but I write them the same way as I do in windows. 

** '** followed by the** letter**.

Best regz,

/g

---

### Post by kleo skywalker on 2008-02-11
> **gvartser said:**
> Ahh oki got it thanks..

I guess it depends on what kind of keyboard layout you are using, but I write them the same way as I do in windows. 

** '** followed by the** letter**.

Best regz,

/g

What followed by the letter? It looks like a single apostrophe.

---

### Post by gvartser on 2008-02-11
I use the swedish keyboard layout and next to (left) the backspace button i have the button with apostrophe left & right.

( ' ) + ( a ) = á 

kind of tricky to explain, but thats how its done on my keyboard.

/g

---

### Post by gvartser on 2008-02-11
Im guessing here but if you are using an English keyboard layout, it could be the key next to the (num 1) key. (left)

/g

---

### Post by Anicka on 2008-02-11
You want to write letters like ä or è or ç or &#269;?
Ok, so option one, is to in the settings System -> Preferences -> Keyboard choose the keyboard you use (or want to mimic using). This can also be done by editing the xorg.conf file.

But if you just want to be able to write one of these once in a while you can go to Applications -> Accessories -> Character map and copy paste or learn the uni-code (also given in the character map) and hold the ctrl and shift keys while typing u0041 to get A or u00e6 to get æ.

gvaster: You use a swedish keybord (and so do I, being swedish in exile) then it easy to do åäöéè since they are either a key on the keyboard or a "preprogrammed" keycombination, but that is not the only letters that exist in the world and not all keyboard layout offers the same possibilities.

---

### Post by kleo skywalker on 2008-02-11
Oh. I use - I'm not even sure - the regular QWERTY layout - the one that's default when installing Ubuntu.

---

### Post by kleo skywalker on 2008-02-11
> **Anicka said:**
> You want to write letters like ä or è or ç or &#269;?
Ok, so option one, is to in the settings System -> Preferences -> Keyboard choose the keyboard you use (or want to mimic using). This can also be done by editing the xorg.conf file.

But if you just want to be able to write one of these once in a while you can go to Applications -> Accessories -> Character map and copy paste or learn the uni-code (also given in the character map) and hold the ctrl and shift keys while typing u0041 to get A or u00e6 to get æ.

gvaster: You use a swedish keybord (and so do I, being swedish in exile) then it easy to do åäöéè, but that is not the only letters that exist in the world.

That works, thanks. Wish it were simpler though.

---

### Post by gvartser on 2008-02-11
Ahh oki, then its sorted,
Nice.

/g

---

### Post by Anicka on 2008-02-11
It is probably the us or "us-international" check here if you want to... [http://en.wikipedia.org/wiki/Keyboard_layout](http://en.wikipedia.org/wiki/Keyboard_layout) but if the default works than that's good. Try to see if you have any dead keys that solves you diacritic problems.

---

### Post by Anicka on 2008-02-11
[http://ubuntuforums.org/showthread.php?t=30070](http://ubuntuforums.org/showthread.php?t=30070)

Look here! It is a description how to bind characters to keys

---

### Post by Kingsley on 2008-02-11
This wouldn't be such a PITA if it alt codes similar to those in Windows were used.

---

### Post by Anicka on 2008-02-11
Well, it is just as much a PITA (as you put it) in windows, it's just that you're used to it, but the big question is why windows have their own system that isn't 100% compatible with unicode...

---

