---
title: "Change the Ubuntu Logo in the menu"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-05-04
Hello,

How can I change the Ubuntu logo that is displayed in the menu bar?

---

### Post by floke on 2007-05-04
You can change it in the gconf-editor - can't remember exactly where the option is - its something like nautilus - apps - panel - global - and then select the menu launcher, select 'custom icon' (something like that) and enter the path to the new icon you want to use.

---

### Post by smokinjoe on 2007-05-17
i just changed my start button

it goes like this:

- type gconf-editor in terminal
- search apps - panel - objects - menu_bar_screen0
- check "use_custom_icon"
- change "menu_type" to "menu-object"

if needed exit gconf-editor and open it again

- enter the icon path in  "custom_icon"



(my first post on linux universe! yaaay! haha)

---

