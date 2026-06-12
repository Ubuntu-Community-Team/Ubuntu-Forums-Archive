---
title: "[SOLVED] Staring a app(Liferea) minimized with no visible window?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by sleepyenglish on 2007-04-19
I use liferea as a audio/video catcher and want it starting up minimized, ive got it starting up but i don't know how to make it start minimized. Its got option to show a icon in the notification area of which ive set and when ubuntu starts up and the liferea window appears the icon is there. Its just as i said i don't want to see the window at start up, i just want the icon in the corner and a popup(which liferea has setting to enable)to alert me to new content.

I'm using Feisty Fawn(which is great by the way), any help will be greatly appreciated, thanks.

---

### Post by moopoo on 2007-10-21
I had the same problem running Feisty and later Gutsy. Google helped me.

Fire up Liferea using the following command:
```
liferea --mainwindow-state=hidden
```

Now it starts minimized with an icon in the tray. Have fun,
moopoo

---

### Post by sleepyenglish on 2007-10-21
Thanks moopoo, it works a treat.

---

