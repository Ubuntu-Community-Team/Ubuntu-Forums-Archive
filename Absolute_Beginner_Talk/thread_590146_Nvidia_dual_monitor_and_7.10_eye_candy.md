---
title: "Nvidia dual monitor and 7.10 eye candy"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by BirdZerk on 2007-10-24
I just upgraded from 7.04 to 7.10 last night and when it rebooted everything worked, in fact PS 7 works even better.  The only thing I am disappointed in, there is no eye candy that the reviews have wrote about.  I was hoping for some of the new default eye candy, nothing special, just some things to make the desktop more fun.  I am using an Nvidia dual monitor card and the Nvidia driver.  Is it possible to activate the eye candy?

---

### Post by Inxsible on 2007-10-24
First you need to use the restricted drivers which I assume you already are.
Second, you can enable Compiz Fusion by, System --> Preferences --> Appearance and selecting Extra or Normal on the last tab(forgot the name of the tab-- I am at work on a Windows Machine :( )

Also, CCSM is not installed by default. Strange, I know !!

so install it by```
sudo aptitude install compizconfig-settings-manager
```Then access it by System--Preferences--Advanced Desktop Effects Manager (I think) -- you'll know what I am talking about once you see it.

Hope that helps !!

---

### Post by Hospadar on 2007-10-24
yep, this is the way to go, you also may want to turn on "Extra" effects first in System->Preferences->Apperance->Visual Effects.  This will give you a good baseline for nice 3-d effects.  Note also that if you want the ever-delightful desktop cube, you'll need to be using 4 workspaces (right-click on the workspace switcher in the lower-right corner of the screen)

---

### Post by BirdZerk on 2007-10-24
I am also running virtualbox, will compiz and virtualbox play together.

---

