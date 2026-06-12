---
title: "[SOLVED] Firefox http://www.%u.com/"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by borimrr on 2007-06-29
Every time I open Firefox it doesn't open my homepage, instead it opens up [http://www.%u.com/](http://www.%u.com/) and says it can't load the page...DUH.

---

### Post by Motoxrdude on 2007-06-29
Type```
firefox
```
into the terminal. 
Im pretty sure its a problem with your launcher because its launching 'firefox %u' instead of just firefox.

---

### Post by lisati on 2007-06-29
Sounds like something got scrambled..... Anyone?

---

### Post by avik on 2007-06-29
Go to the menu editor (Right-click on the main menu, and choose Edit Menus).  Go to Internet, right-click on the Firefox launcher and choose properties.  It should say /usr/bin/firefox %u.  Make sure it's set to that.

---

### Post by alienexplorers on 2007-06-29
Go to Edit>Preferences>Main and check to make sure you have selected show your homepage.

---

### Post by borimrr on 2007-06-29
Right-clicked the icon. Properties>Launcher> Changed firefox %u to firefox. Thx for the responses.

---

