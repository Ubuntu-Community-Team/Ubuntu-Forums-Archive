---
title: "[SOLVED] Remove Input Method from Right Click Menu"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by kucinghitam on 2007-08-29
when i right click in a text box or typing area, i can see 2 menu items at the bottom of the menu; Input Method and Insert Unicode Control Character..how do i remove those 2 menus..? i dont need them at all..

---

### Post by kucinghitam on 2007-08-29
bump! no ones know?

---

### Post by jw5801 on 2007-08-29
You'll need to be more specific. What application are you clicking on text boxes in? Or is it in the Gnome GUI itself?

---

### Post by kucinghitam on 2007-08-29
> **jw5801 said:**
> You'll need to be more specific. What application are you clicking on text boxes in? Or is it in the Gnome GUI itself?
yes..text boxes/typing area in gnome gui..

---

### Post by jw5801 on 2007-08-29
Hmm... I have no idea! Interesting question though, hopefully someone will know.

---

### Post by schorsch on 2007-08-29
Type "ALT+F2" and start the "gconf-editor". Then:

desktop --> gnome --> interface

and disable

show_input_method_menu
show_unicode_menu

---

### Post by kucinghitam on 2007-08-29
> **schorsch said:**
> Type "ALT+F2" and start the "gconf-editor". Then:

desktop --> gnome --> interface

and disable

show_input_method_menu
show_unicode_menu
yes! that's it..it works..thanks schorsch!

---

### Post by schorsch on 2007-08-29
My pleasure ... Can you please mark this as solved?

---

### Post by jw5801 on 2007-08-29
Ah, I figured it would be in gconf-editor, I had a quick squiz around when I came across the question but it wasn't immediately obvious so I moved on! Good work!

---

