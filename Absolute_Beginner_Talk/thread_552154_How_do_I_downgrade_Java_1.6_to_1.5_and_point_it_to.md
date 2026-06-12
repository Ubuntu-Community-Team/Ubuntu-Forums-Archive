---
title: "How do I downgrade Java 1.6 to 1.5 and point it to Azureus startup script?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by dannyboy74 on 2007-09-16
Some guy said that one could try this if Azureus keeps crashing on startup.  He didn't explain that specific how to do all those things.  Can somebody fill in the blanks and guide me through step by step?

> 
if it is 1.6 see if you can get hold of 1.4 or 1.5 java from sun's website and then install the same... and change the azureus start up script to point java to the location which you installed...

---

### Post by por100pre1 on 2007-09-16
I don't know, but I fixed that issue In Azureus by renaming my Azureus settings:

```
mv .azureus .azureus_backup
```

I use Java 1.6 and Azureus from the repositories. Everything is fine here.

---

### Post by dannyboy74 on 2007-09-16
Yeah it was fine for me also for the last couple of months until I accidentally shutdown my PC last night without shutting down Azureus properly first.  Which caused it to glitch and crash everytime I start it up nowadays.

I think I need to uninstall and reinstall Java 1.6 from Synaptic but I don't know which one to pick there's a big list to choose from with Java pakages.  And Add/Remove programs can't do it because it tells me to go to Synaptic instead.

I managed to uninstall and reinstall Azureus but that doesn't change anything.  It's Java 1.6 that needs re-installation.

---

### Post by Delkster on 2007-09-16
Did you try the command por100pre1 suggested? It moves the existing Azureus configuration files out of the way and gives you a fresh start, or so I assume. If the behaviour of the application broke simply by using it, the problem is almost certainly in the per-user configuration (or something else similar) so starting with a fresh configuration might well fix the issue.

Edit: Uninstalling an application generally doesn't remove your configuration files for the application so if you uninstall and reinstall you don't lose your configuration but problems caused by a corrupted configuration file don't go away either.

---

### Post by dannyboy74 on 2007-09-16
Hey moving the .config file did indeed work :)  But now I have a new problem.  How do I resume the torrent which I ran previously on Azureus and then continued on in Ktorrent.

Will it be corrupted because I continued my torrents on different clients.  If not how do I resume it on my newly installed Azureus?

---

