---
title: "original XFCE panel in xubuntu"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-07-06
how can i restore the original panel setup of XFCE in xubuntu?

---

### Post by user1397 on 2006-07-06
[quote=wolfmaniac]how can i restore the original panel setup of XFCE in xubuntu?[/quote]i dont think there's an automatic way to do it, but im sure its not difficult to do it manually.  go [here]("http://shots.osdir.com/slideshows/slideshow.php?release=660&slide=4&title=xubuntu+6.06+screenshots") to see what it looks like.

---

### Post by K.Mandla on 2006-07-06
You can access the panel menu through the Settings Manager. From there you can modify the panels, their size, their attributes and where they sit.

You can move the Workspace Switcher and other stuff by right clicking on them and picking "Move."

---

### Post by aysiu on 2006-07-06
You can try this command: ```
mv ~/.config/xfce4/panel ~/.config/xfce4/panel.backup
``` Then log out and log back in again.

---

### Post by wolfmaniac on 2006-07-06
mv ~/.config/xfce4/panel ~/.config/xfce4/panel.backup

what this will do????

---

### Post by aysiu on 2006-07-06
[QUOTE=wolfmaniac]mv ~/.config/xfce4/panel ~/.config/xfce4/panel.backup

what this will do????[/QUOTE]
Well, if it works, it'll restore the original XFCE panel setup.

If it doesn't, we'll just do this: ```
rm -rf ~/.config/xfce4/panel
mv ~/.config/xfce4/panel.backup ~/.config/xfce4/panel
```

---

### Post by user1397 on 2006-07-06
[quote=wolfmaniac]mv ~/.config/xfce4/panel ~/.config/xfce4/panel.backup
what this will do????[/quote]
you're basically backing up the current setup of your panels, so that when you log out and back in, you'll refresh the desktop.

---

### Post by aysiu on 2006-07-06
[QUOTE=wolfmaniac]mv ~/.config/xfce4/panel ~/.config/xfce4/panel.backup

what this will do????[/QUOTE]
If all goes well, it'll restore the original XFCE panel setup.

If it doesn't go well, you can just do this to get what you have now: ```
mv ~/.config/xfce4/panel ~/.config/xfce4/panel.bad
mv ~/.config/xfce4/panel.backup ~/.config/xfce4/panel
```

---

### Post by Jucato on 2006-07-06
@aysiu: AFAIK, that will only restore your panel to it's original *Xubuntu* configuration. I think what wolfmaniac is saying is that he wants to have an Xfce panel, not the Xubuntu-modified panel. The original Xfce panel doesn't occupy the whole width of the display and no shortcuts/applets on the top panel. The Xubuntu panels are made to mimic Ubuntu's/GNOME's.

---

### Post by wolfmaniac on 2006-07-06
@ yes FENYX interpretated my question correctly!!

any suggestions??????????????:confused:

---

### Post by Jucato on 2006-07-06
Well, AFAIK, the only way is to do it manually. I'll try modifying my Xubuntu install to mimic Xfce. Then I'll try to post what I did. (I'll try... I'm a bit busy)

---

### Post by Jucato on 2006-07-06
How do these look? Good enough? Of course, I didn't use the original Xfce icon set and themes. I still kept the Xubuntu defaults (Industrial Tango theme and Tango icon set).

I had to scale the screenshots down to 640x480, but I'll provide links to the original 1024x768 pics.

A plain, clean desktop:

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntu-xfce1.jpg[/IMG]

[http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntu-xfce1-orig.png]("http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntu-xfce1-orig.png")


This one with some apps open, just to demonstrate the task list (task bar) and system tray.

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntu-xfce2.jpg[/IMG]

[http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntu-xfce2-orig.png]("http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntu-xfce2-orig.png")

---

### Post by wolfmaniac on 2006-07-06
ya gr8!!
so did you created a new panel itself.

i will be giving it a try.

but this issue shud be aressed (to restore the xfce settings in xubuntu)
neway thanx

---

### Post by wolfmaniac on 2006-07-06
how did u added terminal and xfmedia icons??

---

### Post by wolfmaniac on 2006-07-06
in ur 2nd picture u docked the gaim icon on top right most corner of screen.
how did u do it?

---

### Post by Jucato on 2006-07-06
Ok, let's take it one at a time.

1. I didn't make new panels. I just modified the 2 existing ones

2. It's not really an issue. As it is, there is no "pure" Xfce setting/theme, just as there are no "pure" GNOME or KDE settings/themes. Each distro is free to modify the settings/themes as they see fit. It just so happens that Xubuntu devs preferred to make Xubuntu look more lick GNOME rather than Xfce.

3. Right-click on the panel, choose Add Items, then choose Launcher (program launcher with optional menu). In the dialog box that opens, type in *xfterm4* in the Command input area. The icon I used is the default icon. For Xfmedia, type 
*xfmedia* in the Command input area. The icon i used for xfmedia is from /usr/share/icons/hicolor/48x48/apps/xfmedia.png. For the name and description, you can type in anything you want.

4. That's the system tray you are seeing in action, just like the Notification Area in GNOME or the System Tray in KDE. The system tray is already there by (Xubuntu's) default, just to the left the clock's original position. All I did was to remove the frame that surrounds the system tray. You can do that by right-clicking on the system tray, choosing Properties, then unchecking the "show frame" option.

---

