---
title: "Flash on Opera Alpha"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Mazza558 on 2007-10-21
I have flashplugin-nonfree installed...

What's up with it? 

This is the Opera 32bit alpha (9.5). I also tried manuallly installing the flash plugin, but it only reinstalls it for FF.

---

### Post by Maestro23 on 2007-10-21
> **Mazza558 said:**
> I have flashplugin-nonfree installed...

What's up with it? 

This is the Opera 32bit alpha (9.5). I also tried manuallly installing the flash plugin, but it only reinstalls it for FF.

Check the post by Col. K in the following thread:  [http://ubuntuforums.org/showthread.php?t=363878&highlight=flashplugin+in+Opera](http://ubuntuforums.org/showthread.php?t=363878&highlight=flashplugin+in+Opera)

---

### Post by Mazza558 on 2007-10-21
> **Maestro23 said:**
> Check the post by Col. K in the following thread:  [http://ubuntuforums.org/showthread.php?t=363878&highlight=flashplugin+in+Opera](http://ubuntuforums.org/showthread.php?t=363878&highlight=flashplugin+in+Opera)

Thanks a lot, I copied the plugin using gksudo.

---

### Post by yang on 2007-10-21
Something's wrong with mine - all I see is a gray box where the Flash player should be. Pages don't complain about a missing plug-in, though (they do if I disable Plugins in the Quick Prefs, as expected).

I didn't have to copy any files. Opera already had /usr/lib/firefox/plugins in its list of plugin paths. Nonetheless I copied the symlink into the /usr/lib/opera/plugins directory, but no difference.

I'm running Opera 9.50 Alpha (deb install, IIRC) on Gutsy 64.

---

### Post by yang on 2007-10-25
They just released Opera 9.5 Beta today, which fixes this issue (along with others!). However, it seems to actually crash occasionally, which is something I've never seen in the alpha.

---

