---
title: "different keyboard setup for gedit when started through terminal?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-07-24
Is it possible for the keyboard setup to be different in gedit when opened from the terminal vs. opened from the desktop? I'm having a problem with double quotes which I fixed when I ran gedit from the desktop by changing the keyboard layout, now when I run it as a superuser from terminal none of my highlighting works and scripts don't run properly

---

### Post by MrHippocampus on 2007-07-24
The problem is probably not because you run gedit from a terminal, its because your running it as the super user. Just like another normal user the super user has its own configuration files separate from your normal user, I think the only way to get it to work nicely would involve setting up everything again for root the same way as you did for your normal user :(

---

### Post by woodsonoversoul on 2007-07-24
How would I do that through terminal?

---

### Post by woodsonoversoul on 2007-07-24
bump

---

### Post by MrHippocampus on 2007-07-24
I cant think of an easy way to do it as its all done through a gui, my only suggestion is to login as root from gdm and set up everything how you like it.

---

### Post by woodsonoversoul on 2007-07-24
sorry, what's gdm?

---

### Post by MrHippocampus on 2007-07-24
gdm is the login manager, its the place where you enter your username and password before gnome appears.

---

### Post by woodsonoversoul on 2007-07-24
When I configured it originally (correctly) I was logged in as root...

---

