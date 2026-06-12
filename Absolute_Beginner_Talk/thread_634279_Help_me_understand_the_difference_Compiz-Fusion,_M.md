---
title: "Help me understand the difference: Compiz-Fusion, Metacity etc etc"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-07
When I apply a "theme" from System>Preferences>Appearance what am I using?

I also have something installed named "Emerald Theme Manager" with a number of themes listed but I can't seem to figure out how to apply them.

Also, am I using something called Metacity?  Or GTK?  Or what? :)

---

### Post by rickycodie on 2007-12-07
its hard to say what you are using now, i can't see your desktop. 
a good way to tell is if you have any sort of transparency, you are using emerald.

compiz is a windows manager, not a theme manager so it enables different effects on your desktop. try pressing ctrl+alt+left, if it scrolls smoothly then you're using compiz

---

### Post by PeterJS on 2007-12-07
> **Mramius said:**
> When I apply a "theme" from System>Preferences>Appearance what am I using?

I also have something installed named "Emerald Theme Manager" with a number of themes listed but I can't seem to figure out how to apply them.

Also, am I using something called Metacity?  Or GTK?  Or what? :)

You are using both Metacity and GTK. These programs preform different functions, Metacity is the window decorator and controls the title bar, the close buttons etc, and the border around applications. GTK is a widget tool kit and controls the look of UI elements like buttons, scroll bars, etc.

Compiz-Fusion is a couple of things all rolled in to one. It's main function is as a composite manager that controls graphical effects for the desktop environment. Compiz also has a built-in window manager named Emerald. If you're using Emerald it will replace Matacity as the window manager/decorator. Emerald has it's own seperate themes, which usually have semi-transparent portions and other cool effects that  can only be accomplished with a composited environment.

---

### Post by Mramius on 2007-12-07
Hi Peter, hi Ricky...

This is my desktop:
[http://img508.imageshack.us/my.php?image=screenshot1oz7.png](http://img508.imageshack.us/my.php?image=screenshot1oz7.png)

If I download a theme from:
[http://themes.beryl-project.org/](http://themes.beryl-project.org/)

Which program do I use to install it?

What about from this menu?

[http://img507.imageshack.us/my.php?image=screenshotemeraldthemerwr9.png](http://img507.imageshack.us/my.php?image=screenshotemeraldthemerwr9.png)

Clicking on them does nothing and none of those themes are listed where I DO change my themes, which is here:

[http://img515.imageshack.us/my.php?image=screenshotappearanceprerl3.png](http://img515.imageshack.us/my.php?image=screenshotappearanceprerl3.png)

So, basically, what is the difference between those two things?  I know I sound obtuse but I really appreciate the help.

---

### Post by SunnyRabbiera on 2007-12-07
Yeh you are using compiz but by default it uses metacity window decorations.
to install beryl themes you will need the emerald manager and apparently you have that.
basically you cannot use the main control center to install emerald themes, so you need the emerald manager.

---

### Post by Mramius on 2007-12-07
Hmm, I seem to have messed something up.  I typed 'emerald --replace' and I'd like to get it back to how it was...which was the default way, out of the box settings from a fresh install.

---

### Post by LowSky on 2007-12-07
```
metacity --replace
``` this should fix everything

---

### Post by Mramius on 2007-12-07
If I do that, effects like transparent terminal go away.  Which I had *before* doing all of this anyway.

---

### Post by Mramius on 2007-12-07
Editing /usr/bin/compiz helped me here.

I edited the line that says "Use emerald by default" to No.

---

### Post by rickycodie on 2007-12-16
right on i'm glad you got it going!

---

