---
title: "Error relating to gnome-display-properties config from Preferences-&gt;Screen Resolution"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by lars30 on 2007-06-22
I'm working on getting my new widescreen LCD monitor to work on this installation of Ubuntu 7.0

I've not done anything unusual to xorg.conf that I can see, and I've edited that file on other installations. (attached)

Now whenever I click Preferences->Screen Resolution I get the error in the screen capture image below.

I've no idea where to begin to fix this.

Any ideas?

---

### Post by NeoLithium on 2007-06-22
I found this thread, that may be of some help to you:
[http://ubuntuforums.org/showthread.php?t=181586](http://ubuntuforums.org/showthread.php?t=181586)

---

### Post by lars30 on 2007-06-23
Great! I found the gconf editor but couldn't make any changes ("this feature coming soon") but didn't know where to actually affect the change.

I'll try this (from the other issue you referenced) on Monday when I'm back at the office.

> After some more poking around, I found this key in my gnome configuration

~/.gonf/desktop/gnome/screen/0/default/%gconf.xml

Getting rid of the /screen folder solved the problem.


Thanks for the quick suggestion!

---

### Post by lars30 on 2007-06-25
Well, no love.

I deleted the entire ~/.gconf directory for good measure an it had no effect.

It does make the changes despite the error, so it's a nuisance thing at this point.

---

