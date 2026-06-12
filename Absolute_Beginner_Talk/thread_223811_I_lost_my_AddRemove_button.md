---
title: "I lost my Add/Remove button"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-07-26
When I click Applications, on the bottom of the menu there used to be an Add/Remove Programs button, it disappeared.  I have no idea what I did to lose it, but can anyone help me get it back?  I used it a lot, it would be great to have back.

---

### Post by aysiu on 2006-07-27
Right-click on **Applications** and select **Edit Menus.**

Check **Applications** and check the box next to **Add/Remove**

If there is no Add/Remove, go to **File** and select **New Entry**. The command should be ```
gksudo gnome-app-install
```

---

### Post by gamma on 2006-07-27
I noticed I had this happen when I created a new account. The user didn't have access to sudo for some reason by default and it wasn't displaying. Is this a new user account?

---

### Post by CeeDub on 2006-07-27
There it is.  How did I manage to screw that up. Thanks for your help.

---

