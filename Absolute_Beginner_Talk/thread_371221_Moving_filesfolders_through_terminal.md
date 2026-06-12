---
title: "Moving files/folders through terminal"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Pai on 2007-02-26
Earlier I tried dragging a folder to a different location, only to receive an error stating that I didn't have permission to do so.

I figure I needed to use sudo to gain permission, but I've only done that in the terminal.  Is there a way that I can move files through the terminal?  I'm sure there are some relatively simple commands I just don't know.
Or simply how can I move files or folders to a different directory if I do not have the permission.

Thanks.

---

### Post by Maestro23 on 2007-02-26
This link should help: [http://www.tuxfiles.org/linuxhelp/fileman.html](http://www.tuxfiles.org/linuxhelp/fileman.html)

Good all-around site for people new to linux.

---

### Post by annda on 2007-02-26
there is sudo cp (copy) and sudo mv (move). but be careful!!! if you are not sure what you are doing, write everything down so that you can revert it.

---

### Post by jvc26 on 2007-02-26
You could also do:
```

gksudo nautilus

```
And do it via the GUI.
Il

---

### Post by Ozdemon on 2008-06-25
> **Illuvator said:**
> You could also do:
```

gksudo nautilus

```
And do it via the GUI.
Il

Top tip!  Many thanks.

---

