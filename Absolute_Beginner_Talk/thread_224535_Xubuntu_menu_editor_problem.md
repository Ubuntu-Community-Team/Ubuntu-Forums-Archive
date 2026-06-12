---
title: "Xubuntu menu editor problem"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by tsg1zzn on 2006-07-28
When I start the menu editor in Xubuntu the menu disappears and must be fixed by deleting an empty menu.xml from an hidden folder in the user's home folder.

1. Is this a known bug?
2. How do I edit my menu by hand?

---

### Post by OU812 on 2006-07-28
1. I think it is a bug. I think I've seen other users with the same issue. Search the forums - I'm very certain someone has posted the solution to the bug.
2. To edit by hand, look in /usr/share/applications. All menu entries are named *.desktop. Just pick one, modify it, and save it. If you want an icon, I would suggest storing them in /usr/share/pixmaps.

john

---

### Post by tsg1zzn on 2006-07-28
> **OU812 said:**
> 1. I think it is a bug. I think I've seen other users with the same issue. Search the forums - I'm very certain someone has posted the solution to the bug.
2. To edit by hand, look in /usr/share/applications. All menu entries are named *.desktop. Just pick one, modify it, and save it. If you want an icon, I would suggest storing them in /usr/share/pixmaps.

john

Thank you, you answered my original question, however, if the menu is in /usr/share/applications doesn't that mean that all users are forced to use the same menu?

---

### Post by OU812 on 2006-07-28
I can't remember - I haven't used xfce in awhile. Modify the menu - maybe something minor like changing an icon. Log out and then log in as another user or root, etc. Then take a look at the menu. Sorry, that's all I think of.

john

---

