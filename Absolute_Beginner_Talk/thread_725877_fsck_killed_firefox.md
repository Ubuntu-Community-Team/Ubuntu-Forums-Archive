---
title: "fsck killed firefox"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by D_D_T on 2008-03-16
yesterday, after my mandatory fsck on booting, none of my browsers work. Neither firefox nor epiphany. Things such as GoogleEarth and add/remove programs still work so connection isn't an issue, it's just the browsers.
When i click on them to open them, they start to load (the loading mouse icon appears) but the window doesn't open and the program just doesn't start.
What's happening? Can anything be done?
It was the latest stable version of firefox on gutsy and had never had any probs before

---

### Post by banewman on 2008-03-16
As a work around type in a terminal - 
sudo apt-get remove firefox && sudo apt-get install firefox
fsck might have found errors on the hard disk where /usr/bin is located - so a remove/install will shift where on the disk firefox is placed.
:)

---

### Post by D_D_T on 2008-03-16
I tired this but it won't remove. It says that it has other dependencies, or that there are other things dependent on firefox.

---

### Post by 3rdalbum on 2008-03-16
Instead, go to Synaptic Package Manager, find Firefox, and choose "Mark for reinstallation".

If that doesn't work, try moving the hidden .mozilla directory out of your home directory, start Firefox or Epiphany, and see if that solves the problem.

---

### Post by D_D_T on 2008-03-16
w00t! Yeah this has fixed it! Thank you everybody!

---

### Post by banewman on 2008-03-16
Happy for you :)
Can you mark this thread as solved then please.

---

