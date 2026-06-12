---
title: "How to change the number of workspaces?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by desperado315 on 2008-01-17
I've read a thread with the same problem in this forum. But I have another question here: In Ubuntu Help, it shows me another way to change the nr of workspaces by using this comment:
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type int \
  --set /apps/metacity/general/num_workspaces 4

I want to generate 4 workspaces. When I ran this, nothing happened. Anyone knows? Thanks in advance

---

### Post by lswest on 2008-01-17
if you have a workspace switcher on your gnome panel, right-click and choose properties and change the number of workspace you have.

if that doesnt work i'll check out the code later when i'm back on my linux partition.

---

### Post by sailor2001 on 2008-01-17
right click bottom panel and 'add to panel' click on workplace switcher

---

### Post by desperado315 on 2008-01-17
wow, it is really simple but I didnt know, what a shame.
Thanks guys

---

### Post by rungss on 2008-03-02
> **lswest said:**
> if you have a workspace switcher on your gnome panel, right-click and choose properties and change the number of workspace you have..

or right click on the Workspace Switcher and click on the **Preferences** which will most probably be in the top of the popup menu.

Note: Posting this as contribution to documentation..

---

