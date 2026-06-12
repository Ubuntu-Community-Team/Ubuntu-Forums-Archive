---
title: "Version question."
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by lawentzel on 2008-02-06
I have been using the latest and greatest versions of Ubuntu ever since 
I've discovered it.  Since doing so, I have found that earlier versions 
like my hardware a lot better then the newer.  However, I have grown fond 
of having the latest software versions.  So...

If I install version 6.06 of Ubuntu on my system.  Is there an easy way 
to still get the latest versions of software (like Gimp, Inkscape and 
such) without having to actually download it off of the developers 
website and compiling it on my system?  Such as through Synaptic?

Any feedback would be appreciated.  Thank you.

Lee

---

### Post by argraff on 2008-02-06
I don't know, but I'd be interested in the answer to this as well - my old Dell laptop has decided to ONLY like 6.06 (loads and runs like a champ!) and has massive screen issues with everything else! (In Xubuntu, asking to open the terminal crashes everything).

I would like to keep it as a backup machine in case my shiny lenovo goes down, but would need the latest software as well (compatibility - mostly Scribus).

---

### Post by p_quarles on 2008-02-06
Yes, but I don't particularly advise it. Basically, if you installed a significant number of new packages, you'd be defeating the purpose of running the LTS version.

Anyway, you can mix APT-based repositories:
[http://forums.debian.net/viewtopic.php?t=15612](http://forums.debian.net/viewtopic.php?t=15612)

Again, I don't tihnk it's a particularly good idea.

---

### Post by emarkd on 2008-02-06
The software packages you're referring to are called backports.  Not everything is easily backported, so the backports repository is usually a little thin.  You can see the contents of the Dapper backports repository here:  [http://packages.ubuntu.com/dapper-backports/](http://packages.ubuntu.com/dapper-backports/)

---

