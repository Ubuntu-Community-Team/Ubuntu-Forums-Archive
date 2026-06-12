---
title: "[SOLVED] setting preferred sound card"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-12-06
I have two sound cards, one onboard Intel and one pci card, which I prefer.
I can never guarantee which one the pc will start up with which means swopping the connection.
Is there a simple method of setting the preferred card to be used every time?
benbow@benbow-desktop:~$ asoundconf list
Names of available sound cards:
Intel
CMI8738

---

### Post by Lucifiel on 2007-12-06
Hmmm... there should be an option in the BIOS for disabling onboard sound. Have you tried it yet?

---

### Post by eggdeng on 2007-12-06
You could try

```
sudo asoundconf list
``` to get the names of available cards. Then

```
sudo asoundconf set-default-card name_of_card
``` to set the default.

---

### Post by Benbow on 2007-12-06
Thanks Lucifel, Eggdeng's reply solved the problem.

---

