---
title: "xfce panel problems"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by muggins on 2007-07-27
My xfce panel is broken in xubuntu, I can get it back by going to /usr/bin/xfce4-panel and double clicking on it. However when I go to shutdown I do not have any options to choose from other than cancel/quit xfce panel. How do I get my shutdown options back, all I can do now is use the power button on my pc. Also my desktop switcher is missing, how can I get this back too?

---

### Post by ugm6hr on 2007-07-27
> **muggins said:**
> My xfce panel is broken in xubuntu, I can get it back by going to /usr/bin/xfce4-panel and double clicking on it. However when I go to shutdown I do not have any options to choose from other than cancel/quit xfce panel. How do I get my shutdown options back, all I can do now is use the power button on my pc. Also my desktop switcher is missing, how can I get this back too?

Panel:
Press Alt-F2:
type *xfce4-panel &*
This should keep the panel forever.  Some people have to add the command to Autostarted applications though.

For desktop switcher:
Right-click the panel (top or bottom) where you want it - Add new item.
Select Pager
You can move it to where you want by right-clicking on the "Pager" and selecting move - then left-click where you want it.  Remember that you need a "Spacer" to put stuff on the right-side.

Shutdown options:
Right-click the "Quit" and select properties. Make sure that the Action box says Quit.  Not so sure about this one...

---

### Post by muggins on 2007-07-27
Thanks for reply ugm6hr

For desktop switcher:
Right-click the panel (top or bottom) where you want it - Add new item.
Select Pager
You can move it to where you want by right-clicking on the "Pager" and selecting move - then left-click where you want it. Remember that you need a "Spacer" to put stuff on the right-side.

When I select pager I get an error message saying - could not open pager module.

---

### Post by ugm6hr on 2007-07-27
Sorry. I haven't encountered that before.  

Do you know how the panel got messed up in the first place?  Have you tried anything else to try and fix it?  Maybe try restarting the computer having done the *xfce4-panel &* command.  Then try reinstalling Pager.

---

