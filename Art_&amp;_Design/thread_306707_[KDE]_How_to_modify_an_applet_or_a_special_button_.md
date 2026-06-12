---
title: "[KDE] How to modify an applet or a special button in the kicker"
date: 2006-11-25
forum: Art &amp; Design
---

### Post by johnny_b_good on 2006-11-25
hello! it's the first post for me in this forum. i don't know if Art & Design is the right section, i'm sorry if it is not. i usually write in the italian one, infact i'm italian. i have a problem that the italian kde users can't solve, so i ask to you: i have a special button in the kicker called system menu. it shows me the important places of my pc, like my home directory and other things...how can i modify this? i want to add some things and modify some others. how can i do it? i've searched in my pc and i've found two files that maybe can help you: the first is in /usr/share/apps/kicker/menuext and the second is in /usr/lib/kde3/kickermenu_systemmenu.la. if you have kde you can open them with kate and watch if they're useful to solve the problem. thank you very much. bye

---

### Post by aidanr on 2006-11-25
if i remember correctly kmenuedit is the menu editor for kde, so type into konsole "kmenuedit"
of course maybe you're talking about something which can't be changed with kmenuedit or the control center, so i can't really help

---

### Post by sebbe1991 on 2006-11-25
add .desktop files to /usr/share/apps/systemview

---

### Post by johnny_b_good on 2006-11-27
thank you very much! that's the right directory...

---

