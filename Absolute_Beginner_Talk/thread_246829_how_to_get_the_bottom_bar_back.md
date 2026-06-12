---
title: "how to get the bottom bar back"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by mexicancupcak3 on 2006-08-29
ok so im new to ubuntu and i was trying to get the them to look like a mac and somewhere down the line i deleted the bottom bar on the main desktop.. :( 
now how do i get it back please im in need of desperate help thanks in advance who can help...

---

### Post by Anonii on 2006-08-29
> **mexicancupcak3 said:**
> ok so im new to ubuntu and i was trying to get the them to look like a mac and somewhere down the line i deleted the bottom bar on the main desktop.. :( 
now how do i get it back please im in need of desperate help thanks in advance who can help...
AFAIK there is no way to restore the exact panel, that means, that you will have to build it yourself, by adding a new panel and then adding the applications and items you want, on it. 

I think that "killall metacity" if you are using GNOME, will temporary (till next X restart) fix this, but I'm not sure, and I also dont know if it will hurt GNOME (even if I highly doubt it.)

---

### Post by mejy on 2006-08-29
First off, I'm pretty sure killall metacity isn't the command your looking for.  All that does is take away the title bar and window borders, but gnome will automatically restart metacity since it is necessary for it's running.

To add a new panel, right click on the top panel and select 'New Panel'. If the panel it makes is not at the bottom you can drag it there.  Now, right click on the bottom panel and chose add to panel.  Drag things on in the order you want - for the default Ubuntu layout, the order is 'Show Desktop', 'Window List', 'Workspace Switcher' and then 'Wastebasket'.

---

