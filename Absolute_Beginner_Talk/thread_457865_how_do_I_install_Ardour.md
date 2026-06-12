---
title: "how do I install Ardour?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by gamer91 on 2007-05-29
I have tried using the synaptic from the top menu, would it work better by using the terminal. is it even compatible with edgy? 

when i ran it (before I removed it) it would give me an error about 'JACK' not running - is this something else i need to sort out.

---

### Post by tgoose on 2007-05-29
Using Synaptic and running apt-get from the terminal are almost identical methods, so either way you install it should be fine. I don't know if version 2 has reached the Edgy repos yet. If not then I'd definitely advise finding the package somewhere on the Web, since 0.9x has a lot of missing features and not nearly such a nice UI.

About JACK: For all audio input/output Ardour uses a piece of software called JACK. That should be in the repos as jackd and as qjackctl (the former does the actual work, the latter is an interface to control it with.) Ardour won't start without jackd running, and the easiest way to make jackd run with the correct settings is by opening qjackctl (called "JACK Control" in the menu.)

Is there any reason you're sticking to Edgy rather than upgrading to Feisty? On Feisty you can use the Ubuntu Studio repos and get a system more optimised for audio work, as well as perhaps more up-to-date audio packages.

---

### Post by gamer91 on 2007-05-29
I haven't got around to upgrading yet, and I are not sure if all my programs will still run well.

---

