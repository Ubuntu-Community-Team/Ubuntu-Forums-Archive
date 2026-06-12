---
title: "Repositories for Feisty Fawn"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by stephentony on 2007-04-26
I have three newbie questions. The first is this. Is it a good idea to add additional repos? If so then would anyone have a safe list for Feisty Fawn? The last question is what would be the easiest way of adding them to Feisty? Can they be added directly to the third-party software located in "Software Sources" by clicking on the add button? That is about it. I just want to say that I have dumped Windows forever and that Ubuntu is now my primary OS. I wish I had done this a long time ago. Installation was surprisingly easy and I've found getting around to be very intuitive. I also feel that my whole experience with Linux has be far more gratifying than with Windows for a variety of reasons. I'll just say that learning the command line makes me feel more involved than I ever did with Windows, if that makes any sense. Anyway, thanks for any help you can provide!

---

### Post by orb9220 on 2007-04-26
> Is it a good idea to add additional repos?

I do it all the time. To add programs that will unlikely be included in ubuntu repo's or bleeding edge stuff you can't get around it.

> The last question is what would be the easiest way of adding them to Feisty? Can they be added directly to the third-party software located in "Software Sources" by clicking on the add button?

Yep that is what I do put there are also terminal commands to add them to the list which is in /etc/apt/sources.lst is the name of the actual file.

Just be sure to backup it up so you have a clean default one.

---

### Post by igknighted on 2007-04-26
It is not advised unless you know what packages are going into the repository, who has access to it, and other such info.  The easiest way to break your system (other than the rm command) is by adding 3rd party repo's without proper understanding what they will do.  Some time ago a repo that many here use (trevino's i think) included a version of a package that if you upgraded would break things.  You must always be careful when adding these.  The best advice I can offer is to add a repo, install what you want from it, and then deactivate it.  Only do you regular updates from the standard repo's.

---

