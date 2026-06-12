---
title: "System Monitor's readings"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Dance Commander on 2006-04-04
I added the System Monitor to one of my panels and I've enabled all of the "Monitored Resources".  I can click on the system monitor (in the panel) and then a window pops up with various settings, nice charts of the resources, etc.  The percentage I get from the panel is always different from the main System Monitor window.  For example, in the panel it says, "Memory: 66% in use of which 41% is cache"  ...  while the System Monitor window states, "User memory: 330.1 MiB of 2.0 Gib 16.3%".  Are these different readings or do I have do configure something so that the numbers match?  Am I reading them wrong?  ](*,)

---

### Post by dcstar on 2006-04-04
[QUOTE=Dance Commander]I added the System Monitor to one of my panels and I've enabled all of the "Monitored Resources".  I can click on the system monitor (in the panel) and then a window pops up with various settings, nice charts of the resources, etc.  The percentage I get from the panel is always different from the main System Monitor window.  For example, in the panel it says, "Memory: 66% in use of which 41% is cache"  ...  while the System Monitor window states, "User memory: 330.1 MiB of 2.0 Gib 16.3%".  Are these different readings or do I have do configure something so that the numbers match?  Am I reading them wrong?  ](*,)[/QUOTE]
There are many sub-definitions of "Memory" in a Linux environment, it is most likely that you are only seeing some which have been presented to reduce the confusion that displaying all of them would entail, for example these are the definitions from the Help file:

Parameter	Description
User	Memory used by non-kernel activities
Shared	Memory used by more than one application
Buffers	Memory used to temporarily store sent or received data
Cached	Memory used to store data for fast access
Free	Memory not currently in use

Now, the summary when you hover over the panel window only seems to give you the Cache percentage of the overall total, whilst the main window gives the User memory component (and no mention of the kernel usage) - so it is not an "Apples and apples" comparison.

You could probably dig around and find exactly what the definitions/usage is in a Debian Linux system, but who has the time for such esoteric things?

---

### Post by Dance Commander on 2006-04-04
Thanks for your reply... and yes, looking such things up would be trivial.  BUT, is it possible to change what the System Monitor displays in the panel?  (BESIDES WHAT CAN BE CHANGED IN THE PREFERENCES).  I can do the obvious... what I am wondering is, if there is a config file that I can modify?

---

