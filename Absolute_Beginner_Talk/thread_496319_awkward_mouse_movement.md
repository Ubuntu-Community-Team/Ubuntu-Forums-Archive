---
title: "awkward mouse movement"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by ese6 on 2007-07-09
I'm running the latest version of Ubuntu on an HP Pavilion dv5000t laptop and am having an odd problem with the behavior of the touchpad. It seems overly sensitive, and no matter how I adjust the sliders in the mouse configuration it still just has this bizarre feel to it. Very hard to be accurate with it, and if I keep my finger still I can see the pointer shaking.

On the same computer, on a different install of Ubuntu (on an external USB drive) I don't have the problem. Is there a way to reset the mouse drivers or something to try to alleviate this? It's driving me crazy!

Thanks!
ese

---

### Post by zabien1970 on 2007-07-09
Are you using the touchpad or an external mouse?

---

### Post by swisscow on 2007-07-09
I believe for the touchpad there are extra configurations in gsynaptics or ksynaptics - you can find them in synaptic  - lots of synaptics.......who says its not confusing!!) I think you may have to do a little tweaking of the xorg.conf file so read up on this - plenty of threads in these forums.

---

### Post by zabien1970 on 2007-07-09
Oops, didn't pay attentionj to what I was reading,
I just went through something similair, check out this thread
[http://ubuntuforums.org/showthread.php?t=492984](http://ubuntuforums.org/showthread.php?t=492984)

---

### Post by ese6 on 2007-07-16
the problem now is I have no /etc/X11/xorg.conf to modify ...

a couple weeks ago when I booted into linux, X failed to start... it said there was a problem with my graphical interface.  I deleted /etc/X11/xorg.conf in hopes that it would just create a default xorg.conf and fix my problem...  well when I rebooted X did start, but now I've noticed that there the xorg.conf is missing... (not sure where it's reading the configuration from?)

i tried running X -config but when I rebooted it reverted back to the bad graphical interface problem... 

any suggestions?
:-)

---

