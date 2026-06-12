---
title: "Help I have lost my bottom tool bar."
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by hps on 2007-09-30
I have put gutsy on two machines, on one it works great but on this machine I have no lower toolbar. I have tried metacity and sudo metacity but in each case nothing happens, I don't see any change at all.  
Any one have an idea that may help me
Thanks.  ps other than that it is working great. 

jp

---

### Post by n3tfury on 2007-09-30
right click on your existing panel and choose "new panel".

---

### Post by hps on 2007-09-30
Thanks I have a bar now,

You guys are great, As a new user I thank all of the people who help with our questions. 
Hopefully some day I will be able to return the favor to others.

---

### Post by RomeReactor on 2007-09-30
Hi. This may be a an issue related to desktop effects, and it has happened to me frequently in Gutsy; try **left-clicking** on the space where the bottom panel should be, and it will probably show up. If it doesn't, try restarting the panels (go to "System->Administration->System Monitor", find **gnome-panel**, right-click on it and select "Kill Process"; then both panels should show up.

If the lower panel still doesn't show up, try restarting the X server (press CTRL+ALT+BACKSPACE). You should probably search and/or post in the [Gutsy section]("http://ubuntuforums.org/forumdisplay.php?f=238") for this particular problem.

---

### Post by n3tfury on 2007-09-30
you're welcome.  do everyone a favor and mark this thread as "solved" by clicking on thread tools>mark as solved.

---

### Post by mavila on 2007-10-04
I had a similar issue - one of my menu bars had completely disappeared. I tried running gnome-panel and got an error that it was already running. from a command line, I typed "ps -A |grep gnome", found the running gnome-panel and then typed (from the CLI) kill -9 xxxx where xxxx is the PID for gnome-panel.

That worked great as gnome-panel then restarted and the menu was back.

Good luck!

---

