---
title: "User previlages"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-12-08
Is possible to prevent a normal user from modifying (editing) his Application menu?

---

### Post by meborc on 2007-12-08
yes it is, you need to change the permissions of the file that comtains the menu configuration in that users home dir to not me writable unless root...

i'm not using gnome, so i have no idea what file that sould be... it is probably somewhere inside .gnome2 or similar

---

### Post by aysiu on 2007-12-08
I'm not 100% sure this will work, but try: ```
sudo chown -R root:root /home/*username*/.local/share/applications
sudo chown -R root:root /home/*username*/.local/share/desktop-directories
```

---

