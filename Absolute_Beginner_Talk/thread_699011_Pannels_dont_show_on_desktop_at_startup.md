---
title: "Pannels dont show on desktop at startup"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by triskit on 2008-02-16
At some point in the last two days, the upper and lower pannels stopped showing up at startup. Only my desktop image is visible. When I Click my desktop cube (Compiz Fusion if that makes a difference...) and manipulate it at all, everything shows up and works normally. This hapens after completely starting the computer up or logging out and back in.

The other strange thing about it is that I can click on the area where the pannels would be and interact normally (except not be able to see) the menus and icons on them.

Any ideas?

Thanks,
Tristan

---

### Post by MasterJS on 2008-02-16
try ```
sudo killall gnome-panel
``` This will stop any running panels. Then try ```
gnome-panel start
```

---

### Post by triskit on 2008-02-16
didnt seem to work...

---

### Post by MasterJS on 2008-02-16
Maybe you set the bars to be completely transparent. Did you do anything in the opacity settings in Compiz?

---

### Post by triskit on 2008-02-16
nope

they show up when i interact with the desktop, so I can see them just fine when they are up 

it just gave me an error message saying that there was an error starting the gnome dameon, so im assuming that that is what it causing the problem...

i restarted the computer again and everything loaded fine... it just takes a while longer than it used to. 

After I log in, it goes to a solid color screen for a while (about 30 seconds) before loding my desktop image and panels just fine...

---

