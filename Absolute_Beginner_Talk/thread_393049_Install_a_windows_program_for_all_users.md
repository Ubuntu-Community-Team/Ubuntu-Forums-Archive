---
title: "Install a windows program for all users?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-03-25
I want to be able to install the windows version of Firefox so I can use shockwave. I want to be able to use the same install for all the users like native kubuntu programs. How do I do this? Do I install it from a different directory?

---

### Post by aysiu on 2007-03-25
I don't know if there's an easy way to do this, but you can always symlink other users to your .wine folder. ```
sudo ln -s /home/username2/.wine /home/username1/.wine
sudo ln -s /home/username3/.wine /home/username1/.wine
```

---

