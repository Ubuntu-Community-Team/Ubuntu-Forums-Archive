---
title: "How to Set Laptop Lid close To shutdown?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by bme on 2007-06-17
How do I set the laptop lid to shutdown when the lid is closed? I only have 3 choices in the power management-Do Nothing,Standby and Hibernate.

---

### Post by mali2297 on 2007-06-17
You can change the action in the configuration editor. Write in the terminal: 
```

gconf-editor

```
(You can also find it through the menus.)

In the editor, go to /apps/gnome-power-manager/action_ac_button_lid and change the action to shutdown, like for some other actions.

---

### Post by bme on 2007-06-17
thanks a lot.I have now also put system tools including the config editor on the applications menu...

---

