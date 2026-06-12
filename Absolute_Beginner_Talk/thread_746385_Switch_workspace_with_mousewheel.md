---
title: "Switch workspace with mousewheel"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by bchen8341 on 2008-04-05
Hi, without compiz I used to be able to switch workspaces easily by hovering the mouse over the workspace switcher and scrolling the mousewheel, is there anyway to do that with compiz enabled? I know I can just scroll the mousewheel over the desktop to switch workspaces, but I rather prefer doing it over the workspace switcher since my windows are maximized most of the time so I don't have access to the desktop.

---

### Post by The Titan on 2008-04-05
> **bchen8341 said:**
> Hi, without compiz I used to be able to switch workspaces easily by hovering the mouse over the workspace switcher and scrolling the mousewheel, is there anyway to do that with compiz enabled? I know I can just scroll the mousewheel over the desktop to switch workspaces, but I rather prefer doing it over the workspace switcher since my windows are maximized most of the time so I don't have access to the desktop.
are you using gnome or KDE?

---

### Post by bchen8341 on 2008-04-05
I am using Gnome. (Oh, and also I just realized that I can't drag windows from one workspace to another in the workspace switcher either, so any help there would also be great)

---

### Post by jomiolto on 2008-04-05
I have the same problem with switching workspaces, but I'm not sure if there is a fix to it: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150443](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150443). It seems that with Desktop Effects enabled you can't switch workspaces by scrolling the mouse wheel over the workspace switcher :( (you can of course use the hotkeys, like Alt+Ctrl+Left/Right, but it's not the same when you're used to using the mouse wheel).

About the problem with dragging windows: do you have the compizconfig-settings-manager package installed? It adds *Advanced Desktop Effects Settings* option to the System > Prefences menu, and through it you can edit the preferences of the Desktop Effects. From there you can probably find an option to enable switching workspace when dragging windows (sorry, I don't know where exactly you can find it there :( ).

Edit: oh, I found the option: its under the Desktop Wall or Rotate Cube (depending on if you use the cube or not) and from both of those you can find Edge Flip Move setting, which allows you to move windows to different workspaces.

---

### Post by bchen8341 on 2008-04-05
Bahh I guess I'll just disable compiz then... Seems I got all excited for nothing.

(Btw, I do have the compiz-config-settings-manager, and I can directly drag windows to adjacent workspaces, but what I meant was that without compiz I could actually drag the tiny boxes _inside_ the workspace switcher from one workspace to another, which was more practical, and with compiz I can't anymore)

---

