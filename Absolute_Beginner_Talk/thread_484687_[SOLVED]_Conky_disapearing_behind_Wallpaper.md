---
title: "[SOLVED] Conky disapearing behind Wallpaper"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by panther_sn on 2007-06-26
Hi I am trying to get some help (see I said I'd need help) I got Conky working no probs, added it to Startup programs in Sessions, everything I thought I needed, well now When I restart computer I log into my profile I see conky load, then my desktop backdrop loads, and conky is lost, Yet It still shows in system monitor as running (shows sleeping, but so does most things in there) and the only way I can see it is by end process, and then reload using <alt> + <f2> .

So not sure how to make it stop disapearing. Any ideas would be greatly recommened.

---

### Post by kerry_s on 2007-06-26
you need to start it after gnome loads, adjust time according to how long your gnome takes to load.

gedit ~/.conky
put

#!/bin/sh
sleep 5
conky

make it executable, in terminal> chomd +x ~/.conky


this will make conky wait 5 seconds before starting

then put the script in the startup session> ~/.conky

---

