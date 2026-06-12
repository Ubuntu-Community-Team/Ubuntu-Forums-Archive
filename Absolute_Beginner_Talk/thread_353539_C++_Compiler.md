---
title: "C++ Compiler"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by oldmanpete on 2007-02-04
Hi all! 

Newbie question but I'm still green to ubuntu and wondered if it comes with a C++ compiler as part of default install off the live CD because i cant seem to find one in applications menu or within 'add/remove' either....

Cheers!

---

### Post by taurus on 2007-02-04
It's on the LiveCD but you need to install it.

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by oldmanpete on 2007-02-04
Thanks for fast response!

I can see the KDevelope C++ IDE now but I'm running gnome and still cant see a compiler even after the above code? Undoubtedly I'm being dumb, but what am I missing?

Cheers!

---

### Post by g3k0 on 2007-02-04
g++ is generally ran in terminal ie g++ freddy -o freddy.cpp 
or something like that.. might have that mixed up a little, its been a while since I used it

---

### Post by oldmanpete on 2007-02-04
Ah sorry perhaps I should of been slightly more clear.

Was looking for an equivalent to Vis C++

---

### Post by g3k0 on 2007-02-04
Well I usually write all my programs in kate or scite (text editors) and compile with g++.  As far as the whole IDE im not too sure what is good.  I have not used much else.  There are quite a few options in Add Programs under develop or whatever.  Play around and find one you like.  Unless someone here has knows of a good one.

---

