---
title: "How to save settings/changes?"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-15
Ok, I finally got everything working just right. Most of it was done very bleary eyed late at night, so I'm not so sure I could recreate all the work. Heck, I didn't understand most of what I did! At this point, I'm terrified of logging out or shutting down because I really, really don't want to start over. How do I save all my current settings and changes, so next time I boot it comes back the same?

---

### Post by aysiu on 2006-05-15
They should already be saved unless you're using a live CD.
If you want to back up your settings, you can back up the /home/bt224 directory.

---

### Post by bt224 on 2006-05-15
Ok, I feel better. How do I do the backup?

---

### Post by aysiu on 2006-05-15
[QUOTE=bt224]Ok, I feel better. How do I do the backup?[/QUOTE] Well, it's really up to you. 

You can always just open up your file browser and highlight the files you want to back up (make sure you include hidden ones--Control-H in Gnome; Alt-V, H in KDE) and copy and paste them to wherever.

You can also paste this command into the terminal: ```
tar -cvvf backup.tar ~/
```

You can also use a backup program like KDar to back things up. KDar is in the repositories. If you have no idea what that last sentence means, go here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by bt224 on 2006-05-15
Ok, cool, will do. Thanks, aysiu!

---

