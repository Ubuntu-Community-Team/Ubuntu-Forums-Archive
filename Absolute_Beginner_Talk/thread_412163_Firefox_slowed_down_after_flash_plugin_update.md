---
title: "Firefox slowed down after flash plugin update"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by dibbz on 2007-04-17
EDIT:- Nevermind it seems to have sorted itselft out now.

---

### Post by dbbolton on 2007-04-17
usually when firefox slows down, it's due to extensions that run inefficiently

---

### Post by bean77 on 2007-10-18
How can one check to see what extensions are to blame?  I just installed several and am having the same problem.

---

### Post by philinux on 2007-10-18
from a terminal run

firefox -safe-mode

---

### Post by bean77 on 2007-10-18
OK, I did that.  What does it do and is it a permanent fix?

---

### Post by bean77 on 2007-10-19
I've removed all of the extensions I added and it is still slow.  What should I do?

---

### Post by dbbolton on 2007-10-19
> **bean77 said:**
> I've removed all of the extensions I added and it is still slow.  What should I do?
give opera a try.

---

### Post by bean77 on 2007-10-20
I will try that but I'd really like t fix this problem.  I really like FF.

---

### Post by dbbolton on 2007-10-20
> **bean77 said:**
> I will try that but I'd really like t fix this problem.  I really like FF.
well, you might try swiftfox or iceweasel. swiftfox is firefox optimized for specific processor architechtures. iceweasel- i don't really know what's different from it and firefox, but i know that it's quicker and all FF extensions are compatible with it.

---

### Post by silkstone on 2007-10-20
If you've updated the Flash plugin, you're supposed to delete xpti.dat which you'll find buried in a sub-sub-directory under .mozilla.

Not sure if that will help, but worth a try.

---

### Post by bean77 on 2007-10-23
> **silkstone said:**
> If you've updated the Flash plugin, you're supposed to delete xpti.dat which you'll find buried in a sub-sub-directory under .mozilla.

Not sure if that will help, but worth a try.

I'll go try that-thank you!

---

### Post by bean77 on 2007-10-23
I deleted it and emptied my trash...after a restart it's the same.  Very sluggish.  And if I do a google image search for something, the images take forever to show up.

---

### Post by alienexplorers on 2007-10-23
Try the following links to see if they resolve your problems:
> [http://kb.mozillazine.org/Flash_plugin](http://kb.mozillazine.org/Flash_plugin)
> [http://forums.mozillazine.org/viewtopic.php?t=288184](http://forums.mozillazine.org/viewtopic.php?t=288184)
> [http://kb.mozillazine.org/Images_or_animations_do_not_load](http://kb.mozillazine.org/Images_or_animations_do_not_load)

You could also try setting up a new profile using:
> firefox -profilemanager
Then Migrate your prior settings to the new profile:
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

### Post by dimbulb1024 on 2007-10-24
I use the Flashblock plugin which prevents flash files from automatically loading, but gives you the option of playing any flash you actually want to see.

---

### Post by bean77 on 2007-11-09
Gah!  None of this is working for me!

Should I try removing and reinstalling?

---

### Post by bean77 on 2007-11-13
bumping...

---

