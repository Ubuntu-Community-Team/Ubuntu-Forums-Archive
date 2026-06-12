---
title: "LiveDVD with ubuntu, kubuntu and fluxbuntu?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by hito1 on 2007-05-31
Is there a way to put the LiveCDs of Ubuntu, Kubuntu and Fluxbuntu in just one LiveDVD?

Thanks.

---

### Post by Sparkster185 on 2007-05-31
I don't think that would work.  When the system went to boot from the DVD I bet it would get confused.

---

### Post by jonward0690 on 2007-06-05
Plus you are dealing with an iso it is a disk image so yea it would just confuse the computer.

---

### Post by tdrusk on 2007-06-05
I think you can with [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1").
[IMG]http://reconstructor.aperantis.com/screenshots/r_live_customization_modules.png[/IMG]
With this it has a custom apt-get command. You can probably put in 
```
sudo aptitude install xubuntu-desktop ubuntu-desktop kubuntu-desktop
```
Download the package from [here]("http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=5").

Fluxbuntu is not in the repositories yet, so you will have to do that separate or find a repository for it, add it to the repository list of Reconstructor, and then add the command.

I'm going to mess with this program a bit.

---

### Post by hito1 on 2007-06-07
> **fuzzyhair said:**
> I think you can with [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1").
[IMG]http://reconstructor.aperantis.com/screenshots/r_live_customization_modules.png[/IMG]
With this it has a custom apt-get command. You can probably put in 
```
sudo aptitude install xubuntu-desktop ubuntu-desktop kubuntu-desktop
```
Download the package from [here]("http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=5").

Fluxbuntu is not in the repositories yet, so you will have to do that separate or find a repository for it, add it to the repository list of Reconstructor, and then add the command.

I'm going to mess with this program a bit.
Whoa! Thanks! :)

---

### Post by tdrusk on 2007-06-08
> **hito1 said:**
> Whoa! Thanks! :)

You're welcome.
Good luck!

---

