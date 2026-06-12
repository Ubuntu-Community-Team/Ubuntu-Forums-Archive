---
title: "[Quesiton]How to place trash on desktop?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by uibesteven on 2007-08-02
anybody knows how to place trash on desktop, using my own icons? it is important to use my own icons. thank you!!!

---

### Post by xpod on 2007-08-02
alt-f2 or terminal
```
gconf-editor
```

Navigate to apps/nautilus/desktop and check/uncheck whatever you want for the desktop

EDIT:You can also pace the config-editor into your systems tools menus by selecting it in your menu editor

---

### Post by uibesteven on 2007-08-02
thank you! the trash has been added to the desktop. but how can i change the icon into my own?

---

### Post by mcduck on 2007-08-02
> **uibesteven said:**
> thank you! the trash has been added to the desktop. but how can i change the icon into my own?

The icon uses what's in your icon theme. So you'd need to replace the images in the theme you are ow using, ot choose some other icon theme.

---

### Post by isaacj87 on 2007-08-02
are you using a personal icon theme (not the default)

---

### Post by xpod on 2007-08-02
If your not happy with the themes available you can always go to gnomelook.org for new ones:)

If you mean chaging the actual icons of a particular theme then it`s a bit more work i think and not something i`ve ever bothered with.

Plenty good themes ....and more to keep me happy as it is:)

---

### Post by uibesteven on 2007-08-02
i'm using tango theme.

---

### Post by uibesteven on 2007-08-02
actually, i just want to replace the trash icon. but it seems it's troublesome. so, i'd better get on well with the trash.:)

---

### Post by Smu on 2007-08-02
..or you can just create a launcher that launches **trash:** and pick whatever icon you want... The only bad thing about this is that you won't be able to empty the trashbin with a rightclick on the icon...

---

