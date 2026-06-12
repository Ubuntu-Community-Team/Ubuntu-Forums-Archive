---
title: "Removing all panels?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Fleece Flamingo on 2008-01-27
Is it possible to remove all of them? Or is the closest thing I can get it making it transparent and how?

---

### Post by bobbybobington on 2008-01-27
You can set the panel to autohide, which will still leave a bit showing. If you have emerald installed, you can edit the theme to disable shadows, so a transparent panel shouldn't show on autohide. You can also look into other window managers, I think xfce doesn't have to have a panel but I forget.

---

### Post by aysiu on 2008-01-27
You remove all of them. First you have to go to System > Preferences > Session and make sure that *gnome-panel* isn't set to reload. Once you do that, then Alt-F2 and type ```
killall gnome-panel
```

---

### Post by seventhc on 2008-01-27
can't you just right click on the panel and choose 'delete this panel'???

---

### Post by Brunellus on 2008-01-27
> **bobbybobington said:**
> You can set the panel to autohide, which will still leave a bit showing. If you have emerald installed, you can edit the theme to disable shadows, so a transparent panel shouldn't show on autohide. You can also look into other window managers, I think xfce doesn't have to have a panel but I forget.
Fluxbox has no panel.  it is, however, not for everybody, as it's pretty bare-bones.

---

### Post by steveneddy on 2008-01-27
Are you going to use another style of launcher system?

Or icons on the desktop?

---

### Post by seventhc on 2008-01-27
If you right click and choose properties then click on the 'background' tab choose solid color, then slide the slider bar all the way to the left. That will make the panel transparent but you will still have your menu. No effects needed for this to work. Recommended over deleting panel.
you can do this for both upper and lower.

---

### Post by phynix on 2008-04-03
Everytime I try to remove the panal it just keeps coming back

---

### Post by taavikko on 2008-04-03
> **phynix said:**
> Everytime I try to remove the panal it just keeps coming back

Why you want to remove panel?
If you really don't need one, just right click on it, Delete panel!

command **killall gnome-panel** just REstarts it.

---

### Post by mister_pink on 2008-04-03
Like someone said, go on System -> Preferences -> Sessions -> Current session and click gnome-panel. Then I guess remove it if you never want it back. Or maybe set it to Style normal so it doesnt restart itself. Then do the killall thing

---

