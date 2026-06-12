---
title: "Problem with file permissions"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by SynapseKDE on 2007-12-25
I am currently having a problem running the game PlaneShift on Ubuntu. When I try to run the game, it says that I don't have permission to run "/opt/PlaneShift/psclient". (Obs.: The game is already installed).

When I was using kubuntu, I used to add the group "games" to my normal user account. On gnome, when I go System -> Administration -> Users and Groups I can't do the same, because the name of that group is missing.

Any ideas?

EDIT: when I open /etc/group it shows this line "games: x :60:andre,root". Yet, the game won't run when I am logged as 'andre'.

---

### Post by taurus on 2007-12-25
Can you change the permissions to /opt/PlaneShift so you can execute programs in there?

```
sudo chmod -R 755 /opt/PlaneShift
```

---

### Post by SynapseKDE on 2007-12-25
I ended up reinstalling it and resetting the owner/group during the installation (the installation puts it in games group by defaut, so I changed it). That worked for me.

But thank you for answering so fastly :D.

(My first working MMORPG yay! xD)

---

