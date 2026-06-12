---
title: "XMMS - Minimize to Tray"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-06
Does anyone know how I can minimize XMMS to the tray like you can with winamp in windows?

I'm using xubuntu. I know when I was using kubuntu that I could do it using kdocker but that was only if I opened xmms with

$ kdocker xmms

But what if I play a song by clicking on it?

---

### Post by guysmiley25 on 2006-12-23
Bump!

---

### Post by kerry_s on 2006-12-23
You can still click kdocker & it will turn into a + sign then just click on the app you want to minimize.

---

### Post by Azakus on 2006-12-24
If you have an icon on your desktop for XMMS, then right click it, click properties, click Launcher, then replace what's there with "kdocker xmms".

---

### Post by Pikestaff on 2007-04-05
This is how I solved this problem:

```
sudo apt-get install xmms-status-plugin
```

Then open XMMS, press Ctrl-P to open Preferences. Then go to the General Plugin tab and activate the status docklet plugin.  Now you should have an icon in the system tray as well as have XMMS minimized with most other applications.  Right click on the icon in the system tray, choose "Toggle Main Window" and then you should be set.

Now if you do click on it to make it show up again, and you want to minimize it to tray again, you'll have to follow that last step again... right click the icon in system tray and tell it to Toggle Main Window.  I'm not sure how to get it to minimize to tray every time yet.

---

