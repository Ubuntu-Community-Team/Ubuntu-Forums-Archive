---
title: "Task Manager???"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-05-29
When I had dapper, I had installed something from synaptic that let me press ctrl+alt+del and get the linux equivalent of the task manager which included processor load and memory usage.  I'm wondering what is the name of that package?  OR if you can suggest an applet that I can install that will display that kind of information all the time on my desktop.  I appreciate all sugestions.  Thanks!

---

### Post by jimrz on 2007-05-29
> **3rr0r said:**
> When I had dapper, I had installed something from synaptic that let me press ctrl+alt+del and get the linux equivalent of the task manager which included processor load and memory usage.  I'm wondering what is the name of that package?  OR if you can suggest an applet that I can install that will display that kind of information all the time on my desktop.  I appreciate all sugestions.  Thanks!

System > Administration > System Monitor is what you are looking for

you can also right click on your panel select add to panel and add the system monitor applet to your panel for easy access

---

### Post by starcraft.man on 2007-05-29
> **3rr0r said:**
> When I had dapper, I had installed something from synaptic that let me press ctrl+alt+del and get the linux equivalent of the task manager which included processor load and memory usage.  I'm wondering what is the name of that package?  OR if you can suggest an applet that I can install that will display that kind of information all the time on my desktop.  I appreciate all sugestions.  Thanks!

I think this is what your looking for, its really just binding it to a key in conf.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME)

That should be it. I don't think you need any package, its just settings.

Oh and if you want to do it via gui, push Alt + F2 and enter in there "gconf-editor". Then look at the path to the key binding (app/etc...) and you can trace it all the way to the specific setting.

---

### Post by ryanVickers on 2007-05-29
there also is a package you can get with [automatix]("http://ubuntuforums.org/showthread.php?p=2732281") that allows for this, but I wouldn't think it's worth installing it just for that.

---

### Post by starcraft.man on 2007-05-29
> **ryanVickers said:**
> there also is a package you can get with [automatix]("http://ubuntuforums.org/showthread.php?p=2732281") that allows for this, but I wouldn't think it's worth installing it just for that.

I don't really see a reason to install automatix, its just keybindings... An additional note, you can set it to launch on something other than control alt delete if you wish, just change it in the command to what you'd like (or in the GUI, both ways work).

---

### Post by ICUR2Ys on 2007-05-29
Another thing you could do is select System > Administration >  move the cursor and right click to place a launcher on the panel.

---

