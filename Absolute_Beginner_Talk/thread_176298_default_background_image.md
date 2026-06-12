---
title: "default background image"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-05-14
What setting(s) defines **new** user's default background image?

only thing useful I could find was
/usr/share/gconf/schemas/desktop_default_applications.schemas

under
<key>/schemas/desktop/gnome/background/picture_filename</key>

But changing default value didn't do a damn thing.
Can I somehow associate background image to Human theme instead?

---

### Post by endersshadow on 2006-05-14
If you simply right click on the Desktop and select "Change Desktop Background," you can change it there.  You can also change it via the System Menu in System>Preferences>Desktop Background.

Hope this is what you're looking for.

---

### Post by mlind on 2006-05-14
[QUOTE=endersshadow]If you simply right click on the Desktop and select "Change Desktop Background," you can change it there.  You can also change it via the System Menu in System>Preferences>Desktop Background.

Hope this is what you're looking for.[/QUOTE]

Thanks for the reply, although it's not quite what I'm looking for.

If I have system with growing number of users, I'd like that every new user would
get the background I define. If I have 50 new users that haven't yet logged in, it's 
quite big task to do manually.

---

### Post by endersshadow on 2006-05-14
Try this:

```
sudo gedit /usr/share/gconf/defaults/10_libgnome2-common
```

Change this line:

```
/desktop/gnome/background/picture_filename	/usr/share/backgrounds/warty-final-ubuntu.png
```

Replace /usr/share/backgrounds/warty-final-ubuntu.png with whatever you want your default image to be.  I suggest that you also store that background in /usr/share/backgrounds/.

---

### Post by arnieboy on 2006-05-14
[QUOTE=mlind]What setting(s) defines **new** user's default background image?

only thing useful I could find was
/usr/share/gconf/schemas/desktop_default_applications.schemas

under
<key>/schemas/desktop/gnome/background/picture_filename</key>

But changing default value didn't do a damn thing.
Can I somehow associate background image to Human theme instead?[/QUOTE]
```
sudo gedit /usr/share/gconf/defaults/10_libgnome2-common
```
and change the value of  "/desktop/gnome/background/picture_filename"
to something of your choice.

EDIT: endersshadow answered before I did. Please ignore.

---

### Post by mlind on 2006-05-14
ah finally, thanks to both of you 8)

---

### Post by daneness on 2006-05-26
Is this the same place where you would set the default theme for new users? I'm making a script to customize Ubuntu after it installs for so I can do mass installations with certain settings.

---

### Post by aysiu on 2006-05-26
By the way, if you're doing mass installations on systems with the same hardware, you might want to consider using PartImage.

---

### Post by mlind on 2006-05-26
[QUOTE=daneness]Is this the same place where you would set the default theme for new users? I'm making a script to customize Ubuntu after it installs for so I can do mass installations with certain settings.[/QUOTE]

at least it looks like it. For Dapper, default settings on that file are
```

/desktop/gnome/background/picture_options       stretched
/desktop/gnome/background/picture_filename      /usr/share/backgrounds/warty-final-ubuntu.png
/desktop/gnome/interface/gtk_theme      Human
/desktop/gnome/interface/icon_theme     Human
/desktop/gnome/applications/browser/exec        firefox
/desktop/gnome/sound/enable_esd         true
/desktop/gnome/sound/event_sounds       true
/desktop/gnome/background/primary_color         #4E3E29
/desktop/gnome/peripherals/mouse/cursor_theme   Human

```

---

