---
title: "Add/remove problem"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by #1slug on 2006-07-12
OK so I tryed to add some music players, and it told me everything was installed. When I went to click on the app tab it doesn't show up, do I have to reboot or something ? sry if this has been asked before, I realy do appreciate ur feedback, thanks.

---

### Post by slimdog360 on 2006-07-12
type the name of the program into a terminal(the way it shows up in synaptic or the add/remove thingy)

---

### Post by Appolusionist on 2006-07-12
> **#1slug said:**
> OK so I tryed to add some music players, and it told me everything was installed. When I went to click on the app tab it doesn't show up, do I have to reboot or something ? sry if this has been asked before, I realy do appreciate ur feedback, thanks.

Sometimes you just have to refresh your Gnome Panel, which would happen if you reboot. You can refresh the panel without rebooting by opening Terminal (Applications > System Tools > Terminal) and entering the following command.

```
killall gnome-panel
```

---

### Post by Spleenie on 2006-07-12
> **#1slug said:**
> OK so I tryed to add some music players, and it told me everything was installed. When I went to click on the app tab it doesn't show up, do I have to reboot or something ? sry if this has been asked before, I realy do appreciate ur feedback, thanks.

One thing to try (in a terminal) is the following

```
killall gnome-panel
```

This refreshes the panel and application menu. If it still doesnt appear, it is possible that your application does not put a menu entry in when it installs. In that case, you can either add an antry using alacarte (menu editor), create an custom application launcher on a panel, or start the program using a terminal

It may appear in the more comprehensive debian menu, but I forgot how I installed that :)

---

### Post by #1slug on 2006-07-12
When I go to addremove by openin through a mp3 file, it asks me to reload which I promptly do but it then tells me my password is invalid, then reloads.. I tryed inputing [c]killall gnome-panel[/c] but still no luck. Do I need to dl these apps manualy or am I missing something here ?

---

