---
title: "HOW to fix..."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by gamer91 on 2007-05-16
This:

---

### Post by Metacarpal on 2007-05-16
Are you trying to open a program, or do you get this message as soon as you log in?
Have you recently installed or removed any software/packages?
What kind of hardware are you running on (make/model of computer if applicable, what sound card, etc)?
Have you had this issue since first installing Ubuntu, or did it just start happening?

The more info you give, the easier it is to help.

---

### Post by Happy_Man on 2007-05-16
You are on Audacity, I presume?

---

### Post by gamer91 on 2007-05-16
> **Happy_Man said:**
> You are on Audacity, I presume?

yes I am, sorry I meant to say that

---

### Post by gamer91 on 2007-05-16
> **Metacarpal said:**
> Are you trying to open a program, or do you get this message as soon as you log in?
Have you recently installed or removed any software/packages?
What kind of hardware are you running on (make/model of computer if applicable, what sound card, etc)?
Have you had this issue since first installing Ubuntu, or did it just start happening?

The more info you give, the easier it is to help.

[LIST]
[*]Audacity
[*]yes, although nothing that would effect it (i think)
[*]Packard bell imedia 1509 (intel P4, sound integrated on motherboard (realtek drivers were shipped with my PC)
[*]ever since I installed audacity[/LIST]

---

### Post by Happy_Man on 2007-05-16
It is then, most likely an Audacity problem. Have you tried Ubuntu Studio? They've got some really great music and video and just plain general editing software on there... maybe one of those could get the job done ok.

---

### Post by Metacarpal on 2007-05-16
This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/337") in the way Audacity uses the sound card.  You have to kill the esd process and make sure no other audio programs (including media players) are running when you open Audacity.

This bug is fixed in version 1.2.6 of Audacity, as found in Feisty Fawn.  I'm not sure if this has been backported to Edgy yet.

---

### Post by gamer91 on 2007-05-17
Ok, i was trying to use audacity to record from freebirth, i guess I'll have to give up on that.

---

