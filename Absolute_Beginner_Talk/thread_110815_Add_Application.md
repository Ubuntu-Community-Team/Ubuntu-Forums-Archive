---
title: "Add Application"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by Jungles on 2005-12-31
Hi everyone,

I've been using Ubuntu for a few weeks now, but only recently installed Automatix to upgrade Firefox to 1.5.  However, when Automatix was installed, my "Add Application" item disappeared from the Applications menu.  I can't find it in System -> Administration either.

I've uninstalled Automatix now, but Add Application hasn't come back.  How do I restore it?

---

### Post by Mustard on 2005-12-31
You could try using the Applications>>System>>Applications Menu Editor to add an entry back in for the 'Add Applications'.  The command that you need to add to the menu is below.

```
/usr/bin/gksudo /usr/bin/gnome-app-install
```

I'm assuming its still installed of course.  If its not installed then you might have to try installing it again as well.

You could just run it from terminal with this command...

```
gksudo gnome-app-install
```

---

