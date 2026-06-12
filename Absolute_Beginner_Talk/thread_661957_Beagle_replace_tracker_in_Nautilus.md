---
title: "Beagle replace tracker in Nautilus?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Mysticle31 on 2008-01-08
I think I might enjoy the extra features of beagle.  However I find that in order to search for files in nautilus I need tracker. 

Can I replace tracker with beagle?  I really want a web page indexing that beagle offers with it's firefox plugin.

---

### Post by napzilla on 2008-01-10
As far as I know, yes. I installed beagle and removed tracker on my system and nothing exploded.

The beagle/tracker decision has been debated for a while on this forum ([http://ubuntuforums.org/showthread.php?t=396985]("http://ubuntuforums.org/showthread.php?t=396985"))

I almost forgot to mention the second part. You may need to install the beagle-search tool to search for files in nautilus.

---

### Post by Paqman on 2008-01-10
There's a few little plugins you can install for Beagle, IIRC. Have a browse through Synaptic under "beagle" and they should show up.

---

### Post by Mysticle31 on 2008-01-10
I just noticed that last time, when I removed tracker becouse it was crashing and hogging the CPU until you killed it, the search feature in nautilus would not work.

So beagle is compatible then?  That search button should work?

---

### Post by Paqman on 2008-01-10
> **Mysticle31 said:**
> 
So beagle is compatible then?  That search button should work?

Absolutely.

---

### Post by Mysticle31 on 2008-01-11
I don't see a beagle-search in synaptic while searching for beagle

I installed beagle beagle-backend-evolution and mozilla-beagle.  

What else do I need to install to make this work?

---

### Post by napzilla on 2008-01-21
Sorry, I didn't clarify that very well. The beagle-search utility is part of beagle. To have an icon persist in your GNOME panel, add the following program call to your sessions (System->Preferences->Sessions):
beagle-search --icon
In order for this to work, the Beagle daemon should also be running. If this line isn't in your sessions, you may need to add it:
beagled
This just launches the Beagle daemon.

If you don't want to use Beagle during every session, you could also launch both those applications from the terminal using the same commands. Place an ampersand (&) after a command to keep it from enslaving your terminal. You could also launch them using <Alt><F2>.

I hope this helps.

---

