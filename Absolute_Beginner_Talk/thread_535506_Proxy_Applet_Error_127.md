---
title: "Proxy Applet Error 127"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Duffadash on 2007-08-26
When trying to make [proxy-applet]("http://dag.wieers.com/home-made/gnome-applets/#proxy-applet") (A program that adds a tray icon in GNOME, which you can click to quickly change between different proxy settings), I get the following error message:
```
duffadash@Hermes:~/Desktop/proxy-applet-0.2.3$ make
mcs -o proxy-applet.exe proxy-applet.cs -r glib-sharp -r gnome-sharp -r gconf-sharp -r gdk-sharp -r gtk-sharp -r egg-sharp -r glade-sharp /resource:pixmaps/proxy-applet.png /resource:pixmaps/proxy-applet-48x48.png /resource:proxy-applet.glade
make: mcs: Command not found
make: *** [proxy-applet.exe] Error 127
```

Now, I'd really like to be able to change my proxy settings quickly, since I do it several times every day (school have a proxy, home does not), therefore I'd appreciate any help you can give; either to get proxy-applet working, or finding a similar program doing the same thing.

---

