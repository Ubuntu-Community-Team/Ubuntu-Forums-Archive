---
title: "Screensaver settings for KDE"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Rhubarb67 on 2007-04-19
I just installed KDE and have been trying to set my desktop.  I finally found the correct menu item and successfully set my desktop to my liking, except for two minor items.

First, I have dual Samsung 730B 17" monitors set to a resolution of 1152x768 and it actually looks like 800x600.  Now, aside from the fact that for now, Ubuntu doesn't support dual monitors, am I possibly missing a corresponding setting ?

Next, I found the setting for the screen saver and thought I had set everything correctly, but when the timer starts the screen saver, what displays is a black screen with a floating white X.

IS there another setting I need to change?

Thanks
Greg

---

### Post by Stickymaddness on 2007-04-19
Have you installed the drivers for your graphics card?

---

### Post by UbuntuniX on 2007-04-19
To manually change your resolution:

Type "sudo gedit /etc/X11/xorg.conf" in terminal/Konsole.
Enter your root password.
When GEdit has opened it, scroll down to the monitor sections.
On each monitor section, put your custom resolution before the others, separate with a space, example:
```
"1280x1024" "800x600"
```

To:
```
"1152x768" "1280x1024" "800x600"
```

Then save, restart XServer (Ctrl + Alt + Backspace), and you should be fine.

---

