---
title: "Evolution : Is It Possible..."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-06-28
Hello.

I've been wondering this for awhile.

I tried to delete Evolution, as I don't use the whole e-mail program bit, and Add/Remove claimed that I had to go into Synaptics to do the deletion. When I tried to delete a part of the program, I believe it was called Evolution-Webcal, it said in order to delete this, I had to delete Ubuntu-Desktop. I don't know much about Ubuntu, but don't you need the desktop to run?

Or am I just trying to delete the wrong files...

Please help me figure this out. I'm getting this whole thing bit by bit, but there still are a few blank spaces for me to figure out.

Thanks ahead of time.

BDKL

---

### Post by mvaniersel on 2007-06-28
You can safely remove ubuntu-desktop, it's an empty package.

ubuntu-desktop depends on all packages that make up the desktop: meaning that if you install ubuntu-desktop, all the individual components are installed too. It's just a way all desktop components are grouped together. But removing ubuntu-desktop by itself doesn't have any effect.

---

### Post by tcoffeep on 2007-06-28
Not even on upgrades?

I looked it up, and it said "recommended you do not delete for upgrade blah blah blah"

---

### Post by randomnote1 on 2007-06-28
I think it would be easier to run from a command line

sudo apt-get remove evolution

it's a lot more intuitive than the gui I think

---

