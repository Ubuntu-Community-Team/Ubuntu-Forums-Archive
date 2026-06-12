---
title: "repository lists...."
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-11-22
which repositories consider good and you have also installed in your systems...?

---

### Post by someoneouthere on 2007-11-22
...and (maybe if they do) which purpose they represent...?

---

### Post by overdrank on 2007-11-22
> **someoneouthere said:**
> ...and (maybe if they do) which purpose they represent...?

Edgy, Feisty, Gutsy?

---

### Post by AlanRogers on 2007-11-22
It depends very much on what you want:[list=1]
[*]If you want a system that is entirely FOSS compliant, then leave things exactly as they are
[*]If you want the full Ubuntu experience, enable Universe and Mulitverse
[*]If you want other functionality, such as Wine, Skype, Google apps, use their official 3rd party repositiories, usual caveats apply.
[/list]
You do what you want; that's the beauty of Linux.

---

### Post by Paul820 on 2007-11-22
I only use the ones provided with the gutsy install, main, universe, restricted and multiverse. I don't like to use any others sources because 1) i get all what i need from the ubuntu repositories, and 2) i don't want to use sources that i don't trust.

---

### Post by someoneouthere on 2007-11-22
interested in gutsy... 
i want to know about 3party repos like medibuntu and if which of them i can trust...

---

### Post by taurus on 2007-11-22
Medibuntu is all you need besides the standards that come with /etc/apt/sources.list.  Just remove the # sign in front of all the line that have **deb** & **deb-src** at the beginning and you are all set to go.

---

### Post by PmDematagoda on 2007-11-22
Well, from how I used the Medibuntu repos, I can say that they are quite trustworthy repositories, somemore repos would be the Wine repos and the Tux-family.org repos from which I haven't got any trouble yet:).

---

### Post by smacattack on 2007-11-22
medibuntu is trustworthy as far as security goes. it's just the legal issues that may be an issue for some people, depending on their residence.

---

### Post by someoneouthere on 2007-11-22
what i really mean is how many exist ,is there a directory i can find them and some info about them?
propably i can get what i want from the defaults but i thing it is useful to know just in case....

and what about the critiria that a software must consist in order to be added to the repos?

---

### Post by AlanRogers on 2007-11-23
I'm not sure that there is a definitive list of repositories, or I certainly haven't found one, and I have been looking! I suspect that, with the speed at which these things move, any 3rd party list would be quickly out of date.
 
There is a good sources.list [generator here]("http://www.ubuntu-nl.org/source-o-matic/") and I think it's reasonable to assume, by virtue of how long it's been around, that the additions it makes are sound.

---

