---
title: "Fluxbox"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-02-12
I just installed fluxbox but when I log out and select it I get a brown screen. What should I do ? Re-install ?

---

### Post by bluevoodoo1 on 2006-02-12
I'm familiar with Blackbox, and Fluxbox is based on it.... 

Can you right click to open the menu?

The brown screen could be the 'default' wallpaper that gets set if you don't set one yourself.

Are there any files in your .fluxbox folder?

---

### Post by xXx 0wn3d xXx on 2006-02-12
no I can't right click anything and I don't know if there is anything in the folder. I just reinstalled so let's see if it works :)

---

### Post by xXx 0wn3d xXx on 2006-02-12
does anyone know what the problem is ?

---

### Post by bluevoodoo1 on 2006-02-12
What about the fluxconf package?

"FluxConf is a simple GTK 2.0 application allowing fast and easy configuration
of the Fluxbox window manager and its keyboard shortcuts.  This package also
includes the fluxkeys, fluxmenu and fluxbare utilities."

---

### Post by xXx 0wn3d xXx on 2006-02-12
I have that installed.

---

### Post by bluevoodoo1 on 2006-02-12
hmm... anyone else have an idea?

---

### Post by dbw on 2006-02-13
when you boot, use ctrl+alt+f1 to go to a terminal different login.  check your /usr/share/xsessions/fluxbox.desktop file.  it should look something like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=This is fluxbox
Exec=/home/(username)/.fluxbox/startup
```

This tells fluxbox to start flux through a personal startup file.  you should also check your /home/(username)/.fluxbox/startup file, at the minimum, it should contain:

```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```

now chmod +x /home/(username)/.fluxbox/startup

does that help?

---

