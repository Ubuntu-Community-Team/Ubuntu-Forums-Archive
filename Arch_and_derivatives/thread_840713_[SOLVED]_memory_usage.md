---
title: "[SOLVED] memory usage"
date: 2008-06-25
forum: Arch and derivatives
---

### Post by ironcitypete on 2008-06-25
Just installed arch since I've herd so many good things about it on the forums here.  So far I like it seems to be faster then ubuntu but i having some trouble with the memory usage/swap. With gnome, firefox, a terminal, compiz, emerald, and awn running I'm using 1878MB of ram.
```
  
             total       used       free     shared    buffers     cached
Mem:          2025       1878        147          0         14       1479
-/+ buffers/cache:        383       1641
Swap:         2055          0       2055

```

When I close programs the memory usage doesn't seem to drop that much. I have used up to 2015MB of ram but the swap has not been used at all and i have noticed some slow downs.

I can post any configuration file that is needed. Any help would be greatly appreciated.

---

### Post by Barrucadu on 2008-06-25
No, you're using 383MB of RAM. If you look, the rest of it is cache, and can be freed up for anything that needs it.

---

### Post by ch_123 on 2008-06-25
God, I remember this confused the hell out of me when I first started using Linux. I'd be using almost all of my PC's RAM yet it would be running smooth. No need to worry mate :)

---

### Post by ironcitypete on 2008-06-25
Thanks for the help.

---

### Post by Barrucadu on 2008-06-25
I'm sure all of us had a "What!?" moment when looking at free :P

---

### Post by ajgreeny on 2008-06-25
Linux and windows use memory in a quite different manner.  Windows frees up memory as soon as the program using it is closed, but linux keeps data in memory even if the program for that data has closed.  It works on the principle that unused memory is wasted memory.  It will, however, free memory as soon as it is needed.

As others have said, your system is running great, so don't worry, all is well!

---

### Post by handy on 2008-06-26
Many people coming from the Windows world think that they should have the maximum amount of free RAM available.

Linux, will use most all of the free RAM available in your box, because it is the FASTEST thing in your box, when it comes down to actually DOING something!

Does THAT make sense?

---

