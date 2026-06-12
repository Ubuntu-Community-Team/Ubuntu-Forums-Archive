---
title: "[SOLVED] Uninstalling"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by carterrocks on 2008-04-06
So I installed google earth, I can't even remember how.  But now I can't install it!  I tried Synaptic, it doesn't show it.  I searched for the files and found a folder called google-earth in /opt (don't ask me where that is).  I googled around and heard that was an uninstaller in the folder but I can't find it.  I need help.  How do I uninstall it?

---

### Post by Seisen on 2008-04-06
To get to /opt just  ```
cd /opt
``` in the terminal and then do ls and the google earth directory should be there if that is where it got installed at. Then once you find the folder run 

```
sh ./uninstall
``` and it should uninstall it.

---

### Post by mick8985 on 2008-04-06
You will have ran the binary you can download from google, You cannot uninstall unfortunately you need to remove the folder and menu entries

edit:
nvm listen to him instead. On another note next time just use the medibuntu repository

---

### Post by carterrocks on 2008-04-06
> **Seisen said:**
> To get to /opt just  ```
cd /opt
``` in the terminal and then do ls and the google earth directory should be there if that is where it got installed at. Then once you find the folder run 

```
sh ./uninstall
``` and it should uninstall it.

This is what I get when I run sh ./uninstall

```
mark@mark-desktop:/opt$ cd /opt/google-earth
mark@mark-desktop:/opt/google-earth$ sh ./uninstall
Could not find a usable uninstall program. Aborting.
```

---

### Post by carterrocks on 2008-04-06
Anyone?

---

### Post by mick8985 on 2008-04-06
Just do what I said.

```
sudo rm -r /opt/google-earth /usr/bin/googleearth
```

and then delete the menu entries
you can check for menu entries in /usr/share/menu/ aswell

There shouldn't be many other files associated with it, perhaps a few icons in /usr/share/pixmaps or /usr/share/icons if you have a few files left over its not the end of the world.

---

