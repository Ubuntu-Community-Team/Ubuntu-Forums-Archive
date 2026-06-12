---
title: "Nautilus goes full screen in ssh -X"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by sab0tage on 2008-10-22
When I make a connection to my server from my mac via ssh -X and run nautilus, it loads in a full screen - but not really nautilus but my ubuntu desktop, but with no menu bar at the top. And clicking the icons on the desktop doesn't do anything.

Here is what happens when I run nautilus
```
sabo@office:~$ nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:9428): WARNING **: Unable to add monitor: Operation not supported

** (nautilus:9428): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:9428): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:9428): WARNING **: Can not get _NET_WORKAREA

** (nautilus:9428): WARNING **: Can not determine workarea, guessing at layout
```

Check these screenshots
[http://www.grabup.com/uploads/5a128594df4d2e0a71f09aac42b7569e.png](http://www.grabup.com/uploads/5a128594df4d2e0a71f09aac42b7569e.png)

[http://www.grabup.com/uploads/5a011e495b55bf5a8e557eafd3446ec0.png](http://www.grabup.com/uploads/5a011e495b55bf5a8e557eafd3446ec0.png)

I've tried 
nautilus --geometry=100x200 

but it just ends up full screen.
I've made sure that no nautilus windows are open in ubuntu, if that matters. I can also run other apps like firefox with no problem.

Any ideas?

---

### Post by miloh on 2009-01-15
I have the same problem...  I want to resize the desktop that shows up when I run nautilus after ssh'ing in to my Hardy Heron install. 





I have been able to get around it for some tasks by using the following (or other applications):

~$nautilus --browser --no-desktop

---

