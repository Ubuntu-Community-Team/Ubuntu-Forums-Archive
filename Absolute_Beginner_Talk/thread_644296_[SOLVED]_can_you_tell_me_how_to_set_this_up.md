---
title: "[SOLVED] can you tell me how to set this up"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by discoade on 2007-12-18
here's a snippet from an on line tutorial 

> In particular, it probably has its *focus     policy* set to "click to focus." This means that     in order for a window to gain focus (become active)     you have to click in the window. This is contrary     to traditional X windows behavior. If you take my     advice and get a 3-button mouse, you will want to     set the focus policy to "focus follows mouse". This     will make using the text copying feature of X     windows much easier to use. You may find it strange     at first that windows don't raise to the front when     they get focus (you have to click on the title bar     to do that), but you will enjoy being able to work     on more than one window at once without having the     active window obscuring the the other. Try it and     give it a fair trial; I think you will like it. You     can find this setting in the configuration tools     for your window manager.where is the configuration tools     for your window manager.? (gnome)

---

### Post by Lostincyberspace on 2007-12-18
System>Preferences>Windows and set the first section to be what you want.

---

### Post by discoade on 2007-12-18
Thank you!

---

### Post by spiderbatdad on 2007-12-18
press Alt-F2 and enter gconf-editor in the dialogue. From gconf-editor navigate to Apps->Metacity->Genral and scroll down to focus_mode. The value is probably "click" If you highlight the entry a discription will appear below, telling you possible values. You can change the value by right clicking the entry and selecting edit key.

---

### Post by discoade on 2007-12-18
and thank you!

---

