---
title: "Screwed up some libraries"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-02-17
Hi,

in order to get a linux game called Sin to run i found a hint how to solve it including this code

cd /usr/lib
ln -s libSDL-1.2.so libSDL-1.1.so

I ran it, the game didn't ran, and now things like youtube don't run properly (no sound etc).

How to i get back to the original state?

THanks a lot, by now I know that it was stupid in the first place, help me out

ANdreas

---

### Post by dcstar on 2008-02-17
> **Djalmahal said:**
> Hi,

in order to get a linux game called Sin to run i found a hint how to solve it including this code

cd /usr/lib
ln -s libSDL-1.2.so libSDL-1.1.so

I ran it, the game didn't ran, and now things like youtube don't run properly (no sound etc).

How to i get back to the original state?

THanks a lot, by now I know that it was stupid in the first place, help me out

ANdreas

Go into Synaptic and reinstall all the libsdl packages you have installed.

---

### Post by Djalmahal on 2008-02-17
Thanks, that worked

---

