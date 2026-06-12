---
title: "[SOLVED] installing gcc 4.2 under feisty and edgy"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Duffadash on 2007-07-28
Me and a friend wants to install our newly bought copies of Darwinia, but to install the [linux version]("http://www.darwinia.co.uk/support/linux.html") we'll need gcc 4.2. Installing this however turned out to not be all that easy, since everything depends on everything else, and going through more than 20 poackages, one a time, to find out what THEY depend on so that we can get that, to finally install it seems just a little to complicated, any way we can install it without all the trouble... A way to automatically download all dependencies or something? Please help us.
Oh, yeah, I'm using Feisty, my friend Edgy Fit...

---

### Post by Mornedhel on 2007-07-28
Do you really need 4.2 ? 4.1 is in the repositories and installing it via apt-get or any other APT mechanism will take care of the dependencies nicely...

---

### Post by Duffadash on 2007-07-28
the game tells us we need it to play it, so yes we do, but I haven't been able to find any source lists to add to apt for either edgy or feisty... So yeah, we really need it...

---

### Post by Mornedhel on 2007-07-28
Eh, you can try and install it from the gutsy package, but I have this sneaky suspicion it might turn into dependency hell.

The Darwinia website mentions an installer shell script, is it the one that requires gcc ? Weird that a commercial, closed-source game should require compiling.

Edition because I FAIL at english.

---

### Post by Duffadash on 2007-07-28
Dependency hell indeed...
It isn't the shell script, it's when actually running the game it gives the following error:
```
den@Spitfire:~$ darwinia 

/usr/local/games/darwinia

/usr/local/games/darwinia/lib/darwinia.bin.x86: /usr/local/games/darwinia/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)


```

---

### Post by Mornedhel on 2007-07-28
I'd see only two ways out :

1. Try and get libgcc1, libstdc++6 straight from the Gutsy repos, since they have them 4.2 fancy bells there. Or
2. Install Gutsy.

But I have this other thread from ubuntu-fr from someone with a Quake4 problem (and the same error message as yours), and someone suggested a solution (no feedback though...) :

En fait, il suffit de renommer les fichiers “libgcc_s.so.1&#8243; et “libstdc++.so.6&#8243; en “libgcc_s.so.1.old” et “libstdc++.so.6.old” dans le répertoire de Quake4 ( /usr/local/games/quake4/ ).

Translated :

In fact, all you have to do is rename the files “libgcc_s.so.1&#8243; and “libstdc++.so.6&#8243; to “libgcc_s.so.1.old” and “libstdc++.so.6.old” in Quake4's folder ( /usr/local/games/quake4/ ).

That sounds much less painful, and it might just work.

---

### Post by Duffadash on 2007-07-28
Thanks a bunch, we'll check if the last suggestied solution works first... But thank you very much for your help.

The renaming thingamabob is-ah working! Thank you once again, and may thou always keep thy towel handy.

---

