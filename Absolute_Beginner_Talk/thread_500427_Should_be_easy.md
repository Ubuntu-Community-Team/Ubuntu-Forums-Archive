---
title: "Should be easy"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by FNDII on 2007-07-13
How do i do this? from the terminal?

[http://ubuntuforums.org/showpost.php?p=2221625&postcount=29](http://ubuntuforums.org/showpost.php?p=2221625&postcount=29)

If so can i see what it looks like so i can cut and past.

---

### Post by robertc36 on 2007-07-13
?????????????

---

### Post by Waappu on 2007-07-13
> **FNDII said:**
> How do i do this? from the terminal?

[http://ubuntuforums.org/showpost.php?p=2221625&postcount=29](http://ubuntuforums.org/showpost.php?p=2221625&postcount=29)

If so can i see what it looks like so i can cut and past.

Open terminal and type```
gconf-editor
```
Then follow those paths in editor> /apps/compiz/general/screen0/options/hsize to 4
/apps/compiz/general/screen0/options/number_of_desktops to 1
and edit keys

---

### Post by robertc36 on 2007-07-13
You got me there you edited your post did not have link too begin with lol (at me- not you)

---

### Post by macogw on 2007-07-13
Or, instead of using gconf, do this
```
sudo apt-get install gnome-compiz-manager
```
and use that program instead (it'll go in system > preferences > compiz manager)

---

