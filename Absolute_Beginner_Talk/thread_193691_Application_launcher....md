---
title: "Application launcher..."
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-06-10
I have a logitach media keyboard.  When I press the media button it opens rythmbox, but I want it to launch xmms.  How can I change it?  Thanks!

---

### Post by aysiu on 2006-06-10
Unfortunately, there's no easy way yet.

One thing you can do is maybe symlink XMMS to Rhythmbox, so when it tries to launch Rhythmbox, it launches XMMS instead.

Assuming XMMS's launcher is in the /usr/bin directory: ```
sudo dpkg-divert --divert /usr/bin/rhythmbox.old --rename /usr/bin/rhythmbox
sudo ln -s /usr/bin/xmms /usr/bin/rhythmbox
```

You could also reassign the key to the command ```
xmms
``` by pressing Alt-F2 and typing ```
gconf-editor
``` go to Apps > Metacity. Then make sure the command # in Keybinding Commands (XMMS) matches the # in Global Keybindings (whatever the name is for your media button is).

---

### Post by echo $USER on 2006-06-10
Nice, I used the first method, and it worked.  Thanks!

---

