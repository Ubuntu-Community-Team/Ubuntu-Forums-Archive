---
title: "Lost my GUI Login!"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-04-24
I upgraded to Feisty and I can't seem to login anymore. I have my terminals but no GUI login. I have access to my terminals however. I tried to restart X but I get a fatal server error saying the server is already active for display 0. How can I get my login screen back so I can log in as a regular user?

UPDATE
-------

I have narrowed it down to my GDM. When I restart X as root I can't run GDM for some reason. It just hangs with my cursor.

---

### Post by arbulus on 2007-04-24
What happens when you type:

```
sudo /etc/init.d/gdm start
```

?

---

### Post by syalam on 2007-04-24
It says  *Starting GNOME Display manager .... [OK]

When I go to CTRL+ALT+F7 the cursor is still waiting...

---

