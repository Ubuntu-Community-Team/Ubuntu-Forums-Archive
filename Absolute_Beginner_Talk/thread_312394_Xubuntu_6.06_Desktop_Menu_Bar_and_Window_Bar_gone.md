---
title: "Xubuntu 6.06 Desktop Menu Bar and Window Bar gone"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by FroStro on 2006-12-04
I am new to the Ubuntu world. I decided to use Xubuntu, because I was installing the OS on an old Presario with only 64 MB RAM. 

Installation went fine. I have been using Abiword with no problems. 

However, today, when I logged in the Desktop Menu bar and Window Selection bar are no longer on the desktop. I don't believe I had changed any settings for the desktop.

Does anyone know how I can get these bars back?

Thank you.

---

### Post by K.Mandla on 2006-12-04
Try this. First, make sure xfce4-panel is running. That's the process that shows the panels on your screen. Enter this in a terminal (or on a console screen by pressing ALT+F2):

```
pgrep -l xfce4-panel
```If it's not there, enter *xfce4-panel* and press return, and possibly your panels will reappear.

If it is there it will return something like this ...

```
5535 xfce4-panel
```That means it's running, but for whatever reason, it's not showing the panels you have set. What we'll do is kill the panel process, remove your old panel configuration file, then restart it. That should force it to start over with a blank configuration, and you can rebuild them from there.

First kill xfce4-panel.

```
xfce4-panel --exit
```Next, let's back up the old configuration file, just to be safe.

```
cp ~/.config/xfce4/panel/panels.xml ~/panels.xml.old
```
Now remove the old configuration file.

```
rm ~/.config/xfce4/panel/panels.xml
```Now restart the panel process, and hopefully fresh panels should appear. 

```
xfce4-panel
```There used to be a bug in Xubuntu that caused the Applications menu to be eaten if you tried to edit it. I don't think this is related, but if you're having that problem too, we can hunt down that bug report for the fix.

And welcome! :)

---

### Post by FroStro on 2006-12-04
Simply running 'xfce4-panel' solved the problem.

Thanks for the help.

---

