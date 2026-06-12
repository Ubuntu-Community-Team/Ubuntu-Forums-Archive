---
title: "Set A Very Limited Account"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by andytof47 on 2007-01-30
Hey I am just wondering how i would go about setting up a very limited user account.....



I don't want them to be able to adjust anything.......beleive it or not especially the task bar position



Like an ftp account - locked into thier desktop,  the icons they see on their launcher bar....

Can this be done?

---

### Post by mikewhatever on 2007-01-30
System->Administration->Users and Groups. Select a user and click Properties. Set up privileges under User Privileges tab. I am not quite sure which one controls the panels though.

---

### Post by steve.horsley on 2007-01-30
You could try googling for "lock down linux" or similar. I know there are ways to do this, but I don't know how. It's used for "kiosk" type situations. I can think of two approaches:

1: arrange to replace their home directory contents every time they log in (or out). 

2: Make lots of the configuration files in the home folder read-only and change the owner to root so they can't write to them.

---

### Post by andytof47 on 2007-01-30
cheers guys will check it out:guitar:

---

