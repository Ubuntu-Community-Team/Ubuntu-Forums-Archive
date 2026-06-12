---
title: "Thunderbird on GNOME and Selected Item Colors"
date: 2010-04-30
forum: Art &amp; Design
---

### Post by dannymichel on 2010-04-30
I don't know if anyone else has notice that when you have a dark 'selected items' background color, even with white text for your gtk theme, the menu; 'file, edit, view, go, message, etc. text stays black in Thunderbird, rendering that item virtually unreadable. Is there a fix for this either than 'pick a lighter color'?
Any help would be greatly appreciated.

---

### Post by slapfish on 2010-06-06
It has been a long time from your post, but for more than a day I'm troubling to fix this on my dark (only black and white) gtk theme. I just noticed that thunderbird's menu isn't a GTKMenu* widget class so anything you change on menu, menu item etc won't affect it. I think we only have to find which widget class control's it and add something like that on the end of gtkrc file:

```
widget_class "*<Thunderbird-MenuBar>*"               style "YOUR menu style entry"
```


If I figure it out I'll let you now...

Regards
D.

---

### Post by MonkeyPants on 2010-06-15
You've probably solved this by now, but there is a fix in this thread: [http://ubuntuforums.org/showthread.php?t=503508](http://ubuntuforums.org/showthread.php?t=503508).

The only downside is that once you've set the menu items' text to be a certain colour, they'll stay that colour even if they are selected. Hopefully someone has found a fix for that too :S.

---

