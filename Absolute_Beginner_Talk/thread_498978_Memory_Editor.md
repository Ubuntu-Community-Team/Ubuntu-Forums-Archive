---
title: "Memory Editor?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by tennisplaya05 on 2007-07-12
Hey, you guys. 

I was wondering, is there a hex memory editor for linux? 


I've been looking, and i've been able to run a windows Mem. Editor in wine, but im not able to use it to edit any programs outside of wine. So i was just wondering if there is a memory editor for linux.


Or is there a way to make wined programs able to access programs outside of wine?

---

### Post by Madpilot on 2007-07-12
Not sure what you mean by 'memory editor' - an extra app to tweak RAM usage?

If so, don't bother - Linux is very good at using system RAM as fully and agilely as possible.

Linux will use your RAM for cache as much as it can, and swap stuff in and out quickly. Just for example, currently my 1GB of RAM is 38% in use by programs, 61% cache. I'm running the usual dozen or so apps, nothing spectacular - browser, music player, Nautilus, bittorrent client, two or three other misc. apps...

If you want ot monitor RAM & other system usage, go System->Administration->System Monitor.

There's also a nice System Monitor applet for your panel - right-click on your panel, select Add To Panel, find System Monitor in the System & Hardware group. Once the applet is placed, right-click on it again to configure it - I show CPU usage, RAM usage, and Network Usage in the bottom-right corner of my screen, next to the Trash & Workspace Switcher.

---

### Post by tennisplaya05 on 2007-07-12
sorry, i wasnt very clear,
i meant like a hex memory searcher/editor

---

### Post by eentonig on 2007-07-12
And why would you need that?

---

### Post by hardyn on 2007-07-12
i cant really see how that would work without causing a segfault... but let us know if you find one.

---

### Post by Blutack on 2007-07-12
Hmm, don't think these guys quite understand what you are asking for.  I don't have any personal experience but here is a nice list I found
[http://www.linuxlinks.com/Software/Editors/Hex/](http://www.linuxlinks.com/Software/Editors/Hex/)
Most of the popular ones will be in the repositories, best thing to do is open Synaptic Package Manager (System --> Administration) and search for them.
Hope this helps!

(Edit - Ghex is in the repos, Bless looks nice but you'd need to compile it.  Probably Ghex is a good bet, gnome project software is usually pretty good)

---

### Post by loko on 2007-07-12
If you are looking for the bless hexeditor, take a look at my post here:

[http://ubuntuforums.org/showthread.php?p=2933938#post2933938](http://ubuntuforums.org/showthread.php?p=2933938#post2933938)

---

### Post by tennisplaya05 on 2007-07-31
yeah, hardyn was right.....the linux architecture isn't really allowing of such a memory editor. 
thanks though. I appreciate it.

---

