---
title: "New Beryl Upgrade 0.1.5"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-01-18
Just now downloaded new beryl from synaptic update, all went well however my beryl settings manager does not work, says 
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in <module>
    import berylsettings
ImportError: No module named berylsettings

any ideas?

---

### Post by useResa on 2007-01-18
The reason and how to resolve it, is displayed from post #1459 onwards in [this thread](http://www.ubuntuforums.org/showthread.php?t=263851&page=146)

Hope this helps and gets everything working again.

---

### Post by mahiyar on 2007-01-18
Beryl starts and everything is fine just that when I try to run beryl settings manager it just does not start, the thread u mentioned talks about beryl at start up. The same problem was not evident in the earlier version.

---

### Post by ronmarley1 on 2007-01-18
Check this thread: [http://www.ubuntuforums.org/showthread.php?t=339335&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=339335&highlight=beryl)
See my post on the second page for the fix.

---

### Post by mahiyar on 2007-01-18
Thanks a lot ronmarley1 beryl-settings-bindings worked for me .....  Thanks again.

---

### Post by ronmarley1 on 2007-01-18
> **mahiyar said:**
> Thanks a lot ronmarley1 beryl-settings-bindings worked for me .....  Thanks again.
Anytime.  Glad I could help.

---

### Post by useResa on 2007-01-18
> **mahiyar said:**
> Beryl starts and everything is fine just that when I try to run beryl settings manager it just does not start, the thread u mentioned talks about beryl at start up. The same problem was not evident in the earlier version.
That was exactly what I was referring to and that is why I indicated to read the thread from post #1459.

Because in post #1460 is mentioned
> I removed beryl-settings.
Then I reinstalled beryl-settings AND beryl-settings-bindings 
*tata* A new beryl-settings dialog appears.

And as a reply in post #1461
> No need to uninstall beryl-settings, just install -bindings and update and all should be fixed.

beta2 comes out tomorrow and we promise we won't make dep errors this time!

Never mind, you have the situation solved now.
Just enjoy Beryl!

---

### Post by thewump on 2007-01-18
Jeez - some major chaos going on right now!   Different people seeing different things, but for me beryl would not work at all.

If you are in the same boat, and if you are like me, and all you want is for Beryl to work again, then this could get you through the current unrest to restore the environment you have become dependent on to work.

Note:

- I don't really know what I'm doing, I just want to get on with my work.
- My settings manager doesn't work ( although before doing this repo change they did following other advice in this thread )
- Settings work as they were before the update.

Basically, I've switched to the SVN repository whatever that means. I followed the steps here:

[http://www.biodesign.com.ar/blog/?p=28](http://www.biodesign.com.ar/blog/?p=28)

Keith

---

