---
title: "[SOLVED] Menu bar gone in terminal, how do I get it back."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by spideygal on 2007-11-11
Well I know why it is gone, however I can not edit prifiles. How do I get it back?

I did this tutorial here 

[http://www.ubuntugeek.com/how-to-create-a-transparent-terminal-session-as-your-desktop-background.html](http://www.ubuntugeek.com/how-to-create-a-transparent-terminal-session-as-your-desktop-background.html)

The unchecking of menubar i what got me messed up and then I chose to make it the default terminal session.

How do I now edit terminal profiles or change between them?

I suspect I could completely remove terminal and then re add it but there should be a simpler method.

---

### Post by ThrobbingBrain66 on 2007-11-11
Hit Alt+F2 and type gconf-editor into the window that pops up.

navigate to apps > gnome-terminal > profiles > default

Tick the box called 'default_show_menubar'

---

### Post by Paul820 on 2007-11-11
Right click inside the terminal and select **edit current profile**, it's under the general tab.

---

### Post by spideygal on 2007-11-11
> **ThrobbingBrain66 said:**
> Hit Alt+F2 and type gconf-editor into the window that pops up.

navigate to apps > gnome-terminal > profiles > default

Tick the box called 'default_show_menubar'


Thanks, that did it for me.

Solved


Both ways work.

Thanks again

---

