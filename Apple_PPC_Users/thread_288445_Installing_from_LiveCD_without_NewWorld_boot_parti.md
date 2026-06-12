---
title: "Installing from LiveCD without NewWorld boot partition"
date: 2006-10-29
forum: Apple PPC Users
---

### Post by gonfunko on 2006-10-29
I'm trying to install Ubuntu on a Mac mini. The installer goes fine until it actually gets to the point of installing, at which point it claims I need a NewWorld boot partition. I have a valid OS X install on the mini, and the general consensus on this forum and elsewhere seems to be to simply continue anyway. Unfortunately, the installer won't let me continue - it just stays at the same screen, repeating the error when I click Forward. To be clear, I'm trying to install off of the 6.10 Live CD.  So, how do I force it to continue? Is there a command line method of installing I could use instead that would work? Any and all help is greatly appreciated.

---

### Post by Torrance on 2006-10-29
Heya,

The LiveCD installer cannot create a boot partition on macs (it can only write to one) - this is a known bug. So your options are to either use a parition program with the LiveCD to create a boot partition before you start the installer (which is a little tricky, but doable) or to use the text-based installer (which is very simple to use).

---

### Post by gonfunko on 2006-10-30
Thanks for the clarification. Is it possible to access the text based installer from the live cd, or do I need to download the main install CD instead?

---

### Post by Torrance on 2006-10-30
You need to download the whole thing again unfortunately. :@

---

