---
title: "[SOLVED] Remove battery status icon in taskbar"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-04-15
I have my own battery status applet added to my panel and I want to remove the default battery status icon in the taskbar. How can I do so?

---

### Post by sayakb on 2008-04-15
> **rkakkar said:**
> I have my own battery status applet added to my panel and I want to remove the default battery status icon in the taskbar. How can I do so?

Right click on it and click Preferences. Click on "General" tab and select "Only display an icon when battery power is critically low".

EDIT: Follow this instead: Open gconf-editor and goto "/apps/gnome-power-manager/ui" and set "icon_policy" to none.

---

### Post by dje on 2008-04-15
You could have a look in System >> Preferences >> Power Management. In the General tab there are some options for the tray icon but none for turning it off, the closest would be to have it appear only when your battery is critically low on power

hope that's some help,
dje

EDIT: LinuxIsInnovation beat me to it

---

### Post by sayakb on 2008-04-15
> **dje said:**
> You could have a look in System >> Preferences >> Power Management. In the General tab there are some options for the tray icon but none for turning it off, the closest would be to have it appear only when your battery is critically low on power

hope that's some help,
dje

EDIT: LinuxIsInnovation beat me to it

Why do I need to? :) You might be more experienced than me :D

---

