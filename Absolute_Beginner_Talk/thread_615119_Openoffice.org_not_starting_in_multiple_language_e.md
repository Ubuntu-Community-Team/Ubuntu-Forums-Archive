---
title: "Openoffice.org not starting in multiple language environment."
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by tonyjazzu on 2007-11-16
Hello there,

Yesterday I've installed a fresh install of Ubuntu Gutsy.

Polish UI for me
Russian for my wife
Lithuanian and english just in case

Language is being selected on the login screen.

Anyway, today openoffice.org stopped starting with a message in lithuanian saying 


User interface language cannot be defined. 


That's it. 

When I uninstalled lithuanian support it showed me the message in english.

```

sudo apt-get remove openoffice* --purge
sudo apt-get autoremove
sudo apt-get clean

```

And then

```

sudo apt-get install ubuntu-desktop (contains openoffice + other stuff uninstalled by previous code)

```

Did not help. I went to languages section of system -> administration - it said to add some files, I did it.
Openoffice.org still does nothing...

I thought if I change my default UI language to some other it might work but no. No success at all.
Any hints? But please, if You want to say - uninstall ooo and reinstall - don't unless You have a different way of doing it, one that has proven to help with THIS problem.


Thank You so much for Your time,
Kind regards,
TonyJazzu

---

