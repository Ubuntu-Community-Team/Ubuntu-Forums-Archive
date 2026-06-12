---
title: "I Screwed my Fonts!!!"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by DizzyTech on 2007-03-12
I was following an Edgy tutorial from [EasyLinux.info](http://easylinux.info/wiki/Ubuntu:Edgy), and installed msttcorefonts, regenerated the cache, and used their configuration to get my fonts working well:  Bad idea.  Now, all of my Ubuntu fonts are msttcorefonts.  Get what's worse:  I uninstalled msttcorefonts.  

So, in my stupidity, I navigated to the /etc/fonts directory and deleted the faulty configs!

Now all of my font's that are supposed to be either Sans or Monospace are ugly defaults!  Aagh!  
All applications (in terminal) tell me "Fontconfig error: Cannot load default config file".

I've regenerated the cache more times than I can count, and Sans and Monospace are still MS fonts, and everything is still ugly.  All GTK-based apps have an ugly Times-like replacement, while the terminal has --- I can't even describe it!

Is there any way for my to restore the default set of fonts, and restore default configuration of fonts, or is my Ubuntu f****ed?

PS:  I've already reinstalled most of the packages having to do with fonts in Synaptic.  I can't purge anything, for the simple reason that it would remove my whole system.

---

### Post by DizzyTech on 2007-03-12
This ends up looking like spam, but I fixed it!

I downloaded the fontconfig-config deb file from archive.ubuntu.com, unzipped the data, and copied the default conf files to the directories, and restarted GNOME.

---

