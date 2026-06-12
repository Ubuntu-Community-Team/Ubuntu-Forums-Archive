---
title: "workspace-switcher: rounded corners and no borders"
date: 2008-12-31
forum: Art &amp; Design
---

### Post by ErikHK on 2008-12-31
I didn't like the look of the workspace-switcher-applet so I started looking into the code and found that they used cairo_rectangle in the libwnck library. I started to write a bit of code that made a rounded rectangle of four arcs (in cairo), and replaced the regular rectangles with these. Here are some different screenshots of my results:

[http://tux.servegame.org/~erikhk/img/gnome-panel-workspace-switcher.png](http://tux.servegame.org/~erikhk/img/gnome-panel-workspace-switcher.png)
[http://tux.servegame.org/~erikhk/img/workspace-switcher-rounded-orig.png](http://tux.servegame.org/~erikhk/img/workspace-switcher-rounded-orig.png)
[http://tux.servegame.org/~erikhk/img/workspace-switcher-rounded.png](http://tux.servegame.org/~erikhk/img/workspace-switcher-rounded.png)

All the colors are exchangeable through .gtkrc-2.0, here's mine:


style "my_workspace_switcher"
{
  fg[NORMAL] = "#1f1f1f"
  fg[SELECTED] = "#1f1f1f"

  bg[NORMAL] = "#1f211e"
  bg[SELECTED] = "#ff75ff"

  base[PRELIGHT] = "#ffa0ff"
  base[SELECTED] = "#ffa0ff"
  base[NORMAL] = "#505050"
  base[ACTIVE] = "#000000"
}

so, what do you think?

---

### Post by smartboyathome on 2008-12-31
Cool, good job. Now, if only you could have rounded corners on the menus.

---

### Post by cammin on 2009-01-02
Or the windows.

---

### Post by smartboyathome on 2009-01-02
> **cammin said:**
> Or the windows.

I thought the window borders could already. :confused:

---

### Post by cammin on 2009-01-02
Rounded corners all seem to be done with pixmaps.
Since there's only 1 bit making things transparent, the rounded edges look horribly jagged.

---

