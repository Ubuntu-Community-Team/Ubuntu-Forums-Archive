---
title: "How do I extract? [Resolved]"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2007-01-01
I am trying to install Cinelerra, but I can't extract the files.  I should be able to right click and then have to option to extract, shouldn't I?   There is no extract there.  Is there something I need to install from Adept Package Manager?   I thought it might be build-essential, so I installed that but still nothing..

I am using KDE by the way.

Russty

---

### Post by Jorge32 on 2007-01-01
What extention is it? I installed once an autopackage. and you needed to do right click, permissions, and activate the executable option, then double click on it and select the option run. It should install it. 
But maybe it isn't your case, so which format is it your package?

---

### Post by Russty of Oz on 2007-01-01
tar.bz2

---

### Post by aysiu on 2007-01-01
Single-clicking or double-clicking the .tar.bz2 should open up Ark, which will give you a purple arrow pointing up (that's the *extract* button). Click that. If you don't have Ark installed (for whatever strange reason), install it: ```
sudo aptitude update && sudo aptitude install ark
```

---

### Post by Russty of Oz on 2007-01-01
Well, I just installed Ark and now I do get the option to extract but the extracting box just sits there with the little thing going round but nothing happens? 

What have I done wrong?  I did an apt-get update as well but still no change.

---

### Post by Russty of Oz on 2007-01-02
it finally worked, it took quite a while though!  I guess I should learn to be patient. ;)

---

