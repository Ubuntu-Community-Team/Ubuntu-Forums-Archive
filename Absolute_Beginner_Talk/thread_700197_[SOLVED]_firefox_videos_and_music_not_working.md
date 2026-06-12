---
title: "[SOLVED] firefox videos and music not working"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by R13120(1&lt; on 2008-02-18
OK so I've been trying the advice i read here on the forum and still don't seem to be able to get videos or music on myspace and though movies will play on you tube they have a tendency to freeze my computer. i did "sudo apt-get install totem-xine" and i have the media player plug in.( and i have tried disabling it with no affect at all) when i right click on the movie screen (which looks like a bad picasso) it lets me see file (options open or quit) edit preference, see movie control options or quit gnash. i don't see an option to open in another player as another user suggested and I'm beginning to feel like an 1D10T though I'm sure i really will when i figure out how to fix it......... i need help..

---

### Post by oedha on 2008-02-18
have you install the restricted-extras.....it was codecs to play media
from terminal :==> sudo apt-get install ubuntu-restricted-extras

---

### Post by mikeyphi on 2008-02-18
Welcome!!
If not already done - do this:

start Add/Remove - select All in the left menu
search for Ubuntu restricted extras
tick box alongside package - select Apply changes (at bottom of menu).

Ask again if there are still problems!!

---

### Post by R13120(1&lt; on 2008-02-18
> **oedha said:**
> have you install the restricted-extras.....it was codecs to play media
from terminal :==> sudo apt-get install ubuntu-restricted-extras

ya when i try this it says "Couldn't find package ubuntu-restricted-extras" wtf?

---

### Post by oedha on 2008-02-18
have you point yours to the servers ?
system - administrationr - software sources
mark all the boxes
the close it....reload it
open terminal :
sudo apt-get update
then :==> sudo apt-get install ubuntu-restricted-extras
how bout it now ?

---

### Post by R13120(1&lt; on 2008-02-18
> **mikeyphi said:**
> Welcome!!
If not already done - do this:

start Add/Remove - select All in the left menu
search for Ubuntu restricted extras
tick box alongside package - select Apply changes (at bottom of menu).

Ask again if there are still problems!!

it came up with "There is no matching application available." and i can't sudo it because it says "Couldn't find package ubuntu-restricted-extras."

---

### Post by R13120(1&lt; on 2008-02-18
> **oedha said:**
> have you point yours to the servers ?
system - administrationr - software sources
mark all the boxes
the close it....reload it
open terminal :
sudo apt-get update
then :==> sudo apt-get install ubuntu-restricted-extras
how bout it now ?

wow thanks i've got the restricted extra now and that is great i've been beating my head against the wall. but still have the same problem,.. no audio or video. maybe i need to restart.

---

