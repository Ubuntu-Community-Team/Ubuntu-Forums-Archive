---
title: "Battery monitor in the notification area?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by crash331 on 2006-08-14
When I first installed Ubuntu, there was an app on the panel called Notification Area.  It had an icon for my battery that told me how much power I hadleft or how long left to charge the battery.  Now I can't seem to find the battery.  The notification area is still there and it will still hold icons like gaim and all that, the battery just won't come back. And it's not the same battery as the one called "Battery Charge Monitor" that you can add to the gnome panel, it's a different icon.

---

### Post by crash331 on 2006-08-14
Oh, forgot to mention, the tooltips for this used to pop up in the top right and it would say stuff like "Your battery is now fully charged".  Now the tooltip is popping up in the bottomright where the workspaces are.

---

### Post by Illusionistx on 2006-08-14
i'm having the same problem. i used to get to the tooltips and battery notfication but then it just stopped and i can't figure out how to get it back. but i'm not getting any tooltips about my battery anywhere.
and it isn't g-p-m or battery charge monitor.

---

### Post by Illusionistx on 2006-08-15
i think i got mine back. it was the gnome-power-manager, which i had running but i don't know why it stopped showing the notifications. 
but i think this has fixed it for the most part anyway:

```
gnome-power-manager --verbose --no-daemon
```

---

