---
title: "3d desktop"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Mangledbmx on 2006-07-19
hello, just got a quick question that is probably very evident but i cant seem to figure out how to launch 3d desktop. ive installed it but it never showed up in my application list.

what do i need to type into the the terminal to start it up?

thanks in advanced for any help you can give!

---

### Post by bwayman on 2006-07-19
I would like to know as well.

---

### Post by Kilz on 2006-07-19
I just installed it, its kind of neat. Open a terminal, type in 
```
3ddesk
```
You can also add it to the menu with Alararte menu editor, I just made a taskbar launcher.

---

### Post by djsroknrol on 2006-07-19
Poofyhairguy had a how-to in the tips & tricks section...search for it...it has a script for a on/off switch along with it...That's the guide I used to install 3ddesk on my rig...

---

### Post by Jucato on 2006-07-19
3D Desktop won't really show in the Applications menu, unless you add it yourself. However, the easiest way to activite/run 3D Desktop is to make a keyboard shortcut for it in *gconf-editor*.

Here are some relevant commands you might want to remember:
```
3ddesk
```
activates/runs 3D Desktop. The first time it's called, it also runs 3ddeskd, the 3D Desktop daemon, which will conveniently be running in the background.

```
3ddesk --acquire
```
wil cycle through your workspaces, taking screenshots of each workspace. This will update what is displayed when you run 3ddesk.

---

