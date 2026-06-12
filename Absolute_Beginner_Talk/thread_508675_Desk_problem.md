---
title: "Desk problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by dimitars on 2007-07-24
when i switch betwen desk this is happening(look at the atachments). What should i do?
ANd one more question. What did i need to run tar (archive) files.

---

### Post by Orochi on 2007-07-24
I'm not sure what the problem is in the screenshot you attached. Ubuntu should be able to unarchve tar files by default. What tar file are you talking about specifically?

---

### Post by dimitars on 2007-07-24
about screen, problem is that there are no bars(toolbars or somethnig).

i'm talking about Vmware.

---

### Post by tomcheng76 on 2007-07-24
thereis a screenshot inside the screenshot
is that they are the bars that your ubuntu is missing?
and is that ubuntu is running inside vmware?

---

### Post by dimitars on 2007-07-24
there is nothing like u said screenshot in screenshot.

I saw now that i downloaded rpm verzion of vmware. how to unarchive rpm file.
Please help me about theese desks.

---

### Post by Cypher on 2007-07-24
You have to use "alien" to convert the RPM to a DEB file to be installed on Ubuntu. Perhaps if you would tell us what you're trying to do with some detail, we might be able to help..

---

### Post by dimitars on 2007-07-24
at the moment desks are more important. I'll deal with rpw somehow. But the desks are important.  Everything i did was adding effects(desktop effects). Help me to solve this problem.

---

### Post by tomcheng76 on 2007-07-24
i just want to get more information, plz be polite

first try ctrl alt F1
follow this to disable desktop effect temporary
[http://ubuntuforums.org/showpost.php?p=2508092&postcount=4](http://ubuntuforums.org/showpost.php?p=2508092&postcount=4)
edit the xorg.conf by
sudo nano /etc/X11/xorg.conf

then press ctrl alt F7 to go back your desktop
and then ctrl alt backspace to restart X server

you should be able to get back your bars ~~

---

