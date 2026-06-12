---
title: "disappearing active panel icons"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by RonKZ on 2007-03-17
This has happened for the 2nd time now and I don't find a fix.  

When rearranging my panel (w=taskbar) icons for active items kinda got in the way, and when I "moved them" they disappeared, with a ghost-frame heading lower-right.  And now no running app/file shows in the panel.  

So how do I get them back without reinstalling and doing all this over again?  I JUST upped from 6.06 to 6.10 x64 and endured 14 hours of dialup download updates.  There must be a better way!:confused:

---

### Post by mahiyar on 2007-03-17
You can try using this command in terminal >killall gnome-panel. Your panel should hopefully reappear correctly.

---

### Post by RonKZ on 2007-03-17
>killall gnome-panel             returned 
[COLOR="Red"]I've detected a panel already running, and will now exit.[/COLOR]

so apparently that would have wiped out the panel entirely, had it been inactive, which of course it is, and so I'm glad that didn't work!  (I have moved everything into a single panel on the left of my screen).

but, trying to be more clear, my preferred-app-icons on the panel are not the problem.  It is only the temp icons normally associated with open windows which do not appear.  Thus attempting to minimize (-) a window zaps it actually minimizes that window into outer space somewhere, or is that lower-right space.  

and now, as I was writing this, I was digging thru Ubuntu/gnome help, from which I found that in "Add to Panel" the "Window List" icon is that which displays the missing icons.  Simply adding that to the panel brought those active icons back!!! Hurray!!

 :guitar: so my issue is resoved, case closed, thank you

---

### Post by mcduck on 2007-03-17
'killall gnome-panel' would only have restarted your panel, it doesn't destroy your own configurations or anything like that..

---

