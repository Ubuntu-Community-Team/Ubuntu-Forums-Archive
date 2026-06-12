---
title: "emerald vs. gtk-window-decorator"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Drone4four on 2007-12-05
right now emerald loads by default when i start compiz fusion....how do i switch the default to gtk-window-decorator?

---

### Post by shafin on 2007-12-05
You're in gutsy?
If so,just uninstall the emerald package.
I'm sure there is some more elegant solution around,but thats what I do.

---

### Post by kpkeerthi on 2007-12-05
In Compiz Config Settings Manager  -> Effects -> Window-Manager -> command
enter 
```

gtk-window-decorator --replace

```

***Make sure you have gtk-window-decorator installed.

---

### Post by Drone4four on 2008-01-08
> **kpkeerthi said:**
> In Compiz Config Settings Manager  -> Effects -> Window-Manager -> command
enter 
```

gtk-window-decorator --replace

```

***Make sure you have gtk-window-decorator installed.

There is no "Window-Manager" in CompizConfig Settings Manager.   I used the search feature.  There is a Window Management section, but there is no option for command.

I have gtk window decorator installed.

---

### Post by Drone4four on 2008-01-08
> **shafin said:**
> You're in gutsy?
If so,just uninstall the emerald package.
I'm sure there is some more elegant solution around,but thats what I do.

I should be able to switch to gtk-window-manager w/o uninstalling the emerald package.

---

### Post by macogw on 2008-01-08
> **Drone4four said:**
> There is no "Window-Manager" in CompizConfig Settings Manager.   I used the search feature.  There is a Window Management section, but there is no option for command.

I have gtk window decorator installed.

It's the "Window Decoration" section

---

### Post by Drone4four on 2008-01-08
Thanks macogw, I finally found it.

I entered gtk-window-decorator in command box, but when I reload the GUI, I still get emerald.  See attached for a screenshot.

---

### Post by macogw on 2008-01-08
add "--replace" (no quotes) after gtk-window-decorator, maybe?

---

### Post by santiagoward2000 on 2008-01-08
Hi!
An easy way to change the window decorator is using **fusion-icon**. It adds an icon  to the tray bar which let's you select the windows manager, decorator and other options. I installed it with this guide:
[http://ubuntuforums.org/showthread.php?p=3163821]("http://ubuntuforums.org/showthread.php?p=3163821")
It's on the 3rd post.
Cheers!

---

### Post by Drone4four on 2008-01-10
macogw: adding --replance doesn't work.  
santiagoward2000: fusion icon isn't in the default gutsy repos.  what repors are you using?

---

### Post by Drone4four on 2008-01-10
Actually I accidentally overlooked santiagoward2000's link to the guide.  nvm

---

