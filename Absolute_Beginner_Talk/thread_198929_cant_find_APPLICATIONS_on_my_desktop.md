---
title: "cant find APPLICATIONS on my desktop"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by sbuntu on 2006-06-18
I pressed ctrl + Alt + F1 to check out command Line.however inorder to get back to the GUI environment on xubuntu i type shutdown now

When i restarted the machine the APPLICATIONS menu that was there before has dissappared.

I log out and log in as super user and find that it is there

how do i get back my APPLICATIONS menu on the taskbar for the normal user

---

### Post by user1397 on 2006-06-18
right-click anywhere on the toolbar, and click "add to panel" and add "menu bar"

---

### Post by johnnymac on 2006-06-18
Right-click the panel and say add....then go down the list to where you find menu.  There's an outstanding issue in XFCE right now (not sure if it's fixed yet) where your menu may disappear.  If you look here:

cat ~/.config/xfce4/desktop/menu.xml

and it is blank - then do this:

cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/

GL

---

### Post by jpkotta on 2006-06-18
It sounds like you don't know how to use the virtual terminals, because you said you shutdown to get back to the X session.  There are six virtual terminals, CTRL-ALT-F1, CTRL-ALT-F2, ..., CTRL-ALT-F6.  X servers use the terminals beyond 6, so you can get back to your X session with CTRL-ALT-F7.  If you start second X server, it will be on CTRL-ALT-F8, etc.

---

### Post by sbuntu on 2006-06-18
I copied the menu.xml exactly as suggested , but i still dont see the application menu

Please help

---

### Post by sbuntu on 2006-06-18
applications menu doesnt appear on the taskbar but when i right click anyhwere on the desktop, i see it

I wonder why...

---

