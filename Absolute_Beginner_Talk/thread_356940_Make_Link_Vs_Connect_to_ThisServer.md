---
title: "Make Link Vs Connect to ThisServer"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-09
when i right click a network folder there are two options:
1] Make Link
2] Connect to This server

Logically Make link should create a shortcut/link on out desktop or home or somewhere to easily access that network folder, but its always fails, whereas connect to this server, works and does what i am expecting of make link, i.e. create a short cut link on desktop for easily accessability, and then i wanna ask that both of these command actually mount the network folder, isn't it?

---

### Post by shoaibi on 2007-02-09
on the network folders that require a user name and password, connect to this server doesn't appear in the right click menu, and the make link doesn't work, do i have to mount manually the folder???

---

### Post by shoaibi on 2007-02-09
was the problem statement notclear or nobody ahs any idea about it?

---

### Post by shoaibi on 2007-02-09
well i just asked the difference :( :(

---

### Post by goatflyer on 2007-02-09
'Make connection' adds an icon and an entry to your 'Places' menu.  When you click on the entry it makes the (samba) connection to the other computer.

'Make link' means make a symlink.  It creates a symlink on the same directory on the target, which you could then move to any other location. (try it on a folder in your own home directory).  However, when dealing filesystems which don't support symlinks (ex: windows over samba) then the symlink creation will fail.

Hope this clears things up for you.

---

