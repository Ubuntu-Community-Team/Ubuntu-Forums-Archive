---
title: "What do I do with all of these folders?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by brightscreamer on 2007-10-12
So, like any new Ubuntu user, I've been installing all kinds of stuff (e.g.; ALSA drivers, AWN, checkgmail, etc.). What do I do with the folders after I install the software? I normally delete the installers on OS X, but these aren't installers. For the time being, I've put them in the Home folder. Is this the right thing to do? I'm still feeling my way around the file system. Thanks!

---

### Post by PurposeOfReason on 2007-10-12
Put them wherever you want. :D

If it's something you can update (such as AWN) just make a folder called programs and just throw them all in there.

---

### Post by Shazaam on 2007-10-12
To keep my desktop somewhat clean (if that is what you are looking for) I make a folder on the desktop and name it something (usually "crap") to stuff stray folders and files into. But you did ok.

---

### Post by Circus-Killer on 2007-10-12
but for most applications (like AWN and checkgmail), i would recommend just using package manager to install them. why you downloading and installing manually?!?

AWN is not in the repos i know, but there are third-party repos that offer it. as for checkgmail, to install it (and others like that, remember MOST applications are available this way), do the following:

open up a terminal and type...
```
sudo apt-get install checkgmail
```

it is recommended to install packages this way, not only will it automagically resolve dependencies, but will also keep the software up-to-date whenever you check your system for updates.

---

### Post by brightscreamer on 2007-10-12
Wow! Thanks for all of the quick replies!

Another question: Do I have to restart the computer after installing programs or is there another way to get them to work right after installation? Pardon my n00bspeak.

---

### Post by drewlake on 2007-10-12
You **should **only need to restart after a kernel update. Most things work straight away.

---

### Post by hyper_ch on 2007-10-12
> **drewlake said:**
> You **should **only need to restart after a kernel update. Most things work straight away.

There are 2-3 more cases that require restart... but restart is required very, very seldom...

---

