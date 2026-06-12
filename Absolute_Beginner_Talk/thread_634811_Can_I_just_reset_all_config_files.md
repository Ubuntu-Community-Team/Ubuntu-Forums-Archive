---
title: "Can I just reset all config files?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by staib on 2007-12-08
Your help is needed!

I can't get Desktop Effects to work on my profile (I loose the top frame from all windows) - the other two users on this box are fine (and I just made a new user and that one too is fine). 

I suspect it's because I had used Beryl and Emerald in the past and used the upgrade path to 7.10 rather than a fresh install...

So - I have tried the good advice on Furlong's blog - but still no joy on my profile.  

Is there a way to delete my current 'display config files' which I assume are somehow corrupt and then allow Ubuntu to reset them to defaults so it all works properly?

Thanks

---

### Post by CatKiller on 2007-12-08
I don't know for sure which ones they would be, but user config files are kept in that user's Home folder. They normally start with a . so that they are hidden by default. You can use Ctrl-H in Nautilus to show the hidden files.

You don't necessarily need to delete the files to get new ones. Renaming them to something else (for example, by appending .backup to the name) and then logging out and back in should work.

Good luck!

Edit: I have a ~/.beryl directory and a ~/.berylmanagerrc file in my Home folder from when I did a similar upgrade. Those would be my first guesses at files to remove. Otherwise, there are some Beryl theme settings in ~/.emerald.

---

