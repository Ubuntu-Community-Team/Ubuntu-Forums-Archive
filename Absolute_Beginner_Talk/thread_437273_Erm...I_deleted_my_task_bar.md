---
title: "Erm...I deleted my task bar"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by mk_gm1 on 2007-05-08
Well...this is kind of embarassing. 

I thought when I clicked 'remove panel', it would get rid of the quick links with links to firefox, and the mail client etc. 

I have access to the terminal if it helps, as I've mapped it to a shortcut...

Please, someone help out this idiot!

---

### Post by mejy on 2007-05-08
Try 'rm -rf ~/.gconf/apps/panel' and then logging out and back in.  I'm sure there's an odd GUI way to do it, but that should work.  Certainly the most interesting request I've read in a while :P

---

### Post by LMP900 on 2007-05-08
I understand that you still have a panel, but your "task bar" is gone, right?

1. Right click the panel
2. Select: "Add to Panel"
3. Find "Window List" and select it
4. Click the "Add" button

That should give you back your task list on the panel. :)

---

### Post by mk_gm1 on 2007-05-08
Thanks a lot - the terminal command thing fixed it. :) Btw, how do you logout from the terminal? I tried 'logout', but it just closed the terminal. So I did a reboot instead.

LMP900: There was no panel to click :P. As in the whole bar that normally sits at the top of your desktop, and has 'applications, places, system' in one corner and the time and the logout button in the other - that whole bar was gone. :/

---

### Post by jyba on 2007-05-08
I did the same as you a couple of weeks ago and it all happened so fast that I never found out how I did it. The solution that I used was the terminal command:

```
kcmshell /usr/share/applications/kde/panel.desktop
```

which brings up the GUI interface for the task panel.

---

### Post by bobplano on 2007-05-08
hunting season for taskbars is in full swing now huh. im just kidding but this seems to be happening more often recently

as long as one bar is there you can add the other one back. i don't remember the exact steps but you right-click on the other one and then you should be able to add it back. that's what LMP900 was talking about

---

### Post by LMP900 on 2007-05-08
> **mk_gm1 said:**
> Thanks a lot - the terminal command thing fixed it. :) Btw, how do you logout from the terminal? I tried 'logout', but it just closed the terminal. So I did a reboot instead.

LMP900: There was no panel to click :P. As in the whole bar that normally sits at the top of your desktop, and has 'applications, places, system' in one corner and the time and the logout button in the other - that whole bar was gone. :/

Ah, okay. I was not aware that you could delete all the panels (the option is grayed out on my only panel). Glad you got it fixed!

---

