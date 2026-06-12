---
title: "Number of Workspaces option disabled"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by maXx_ on 2007-04-26
I'm running the latest Feisty and i went to change the number of workspaces, as told by the built in  helper. i ran 

gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type int \
  --set /apps/metacity/general/num_workspaces 3

and 

gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type int \
  --set /apps/metacity/general/num_workspaces 3

to simply try and get just 3 workspaces, and now i only have one, and cannot add anymore. When I right click and try to change the number of workspaces, the button and scroll thing is just grayed out. 
Any suggestions? 

-maxx

---

### Post by Martin on 2007-04-28
Maybe I've completely misunderstood what it is you're trying to do.
I presume you just want to change the number of workspaces displayed in the workspace switcher in the panel? I thought all you had to do was right click in the workspace switcher - choose preferences and then the number of workspaces
 I'm fascinated as you what told you to type all that in just to change the number of workspaces.

To configure things a little more easily use gconf-editor
 Open a terminal and type "gconf-editor" and choose 'apps' then go down to' 'metacity' then 'genera'l and then change "num_workspaces" to the value you desire.
Cheers

---

