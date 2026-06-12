---
title: "Editing /etc/X11/xorg.conf"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by niallabrown on 2006-08-09
When I enter /etc/X11/xorg.conf from the file system windows it says I'm not permited to edit it.

Some Time ago I used sudo gedit /etc/xorg.conf and that worked then, but now its just giving me a blank screen.

Any idea what im doing wrong?
How do you sign in a ROOT?

---

### Post by klytu on 2006-08-09
> **niallabrown said:**
> When I enter /etc/X11/xorg.conf from the file system windows it says I'm not permited to edit it.

Some Time ago I used sudo gedit /etc/xorg.conf and that worked then, but now its just giving me a blank screen.

Any idea what im doing wrong?
How do you sign in a ROOT?

Did you really type in:

```
sudo gedit /etc/xorg.conf
```

Or did you do:

```
sudo gedit /etc/X11/xorg.conf
```

In the first case, which would be a typo, gedit is creating a new file which didn't exist before and is therefore blank. In the second you are editing the file you wanted to edit. Make sure to back up /etc/X11/xorg.conf before making any changes to it. For example:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

If you make a mistake in this important file you could really mess up your graphics or other essential input/output devices you need for your system to work properly. This way you can restore your working version if you get into trouble.

---

### Post by niallabrown on 2006-08-09
You got it.  Thanks!

---

