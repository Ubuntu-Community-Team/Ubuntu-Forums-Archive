---
title: "networking with mac"
date: 2008-03-20
forum: Apple PPC Users
---

### Post by thespottedelf on 2008-03-20
hey i have 7.0.4 running on a imac g3 500mhz

When i first installed (or reinstalled for the 4th time cause i screwed the others up lol) i could just go to places network, select the mac, type in my username password and boom there it was.

It won't work any more... it doesn't give errors, it just disappears either b4 username + password or after.

any ideas? 

and plz keep it simple... i'm a noob with cli stuff ;)

---

### Post by thespottedelf on 2008-03-21
n1 knows?

---

### Post by slacka-vt on 2008-03-21
make sure you have "hfsplus" installed
it's what enables ubuntu to read a HFS+ filesystem.
use synaptic and search for hfsplus  (one word)
or use the terminal

sudo apt-get update
sudo apt-get install hfsplus

hope that helps
~s

---

### Post by thespottedelf on 2008-03-21
thank you so much :D

worked right away :D

---

