---
title: "Nvidia-Settings not loading on start up"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by vinayan3 on 2006-05-05
Hi,
I loaded the nvidia settings utlity and it does not start up with gnome. I would like it to so my settings for brightness and gamma are applied when my pc boots. It is a tad annoying to manually  open it every time.
Setup:
Ubunutu Breezy
Nvidia 6600 GT AGP
GNome Desktop
Nvidia drivers loaded
Nvidia settings loaded.

Thanks
Vinay A.

---

### Post by yabbadabbadont on 2006-05-05
You will need to add it to the list of startup programs in your session.

System->Preferences->Session.

Then select the Startup Programs tab and click Add.

You will need to call it with the command line option that tells it to just load the stored settings and exit.  I don't have it installed, so I'm not sure what that option is.  Just run the program from a terminal with --help and see what it lists as options.

It should run the next time you logout and back in.

---

### Post by Perfect Storm on 2006-05-05
```
sudo gedit /usr/share/applications/nvidia.desktop
```

add following lines:

[b][Desktop Entry]
Name=Nvidia Settings
Comment=Nvidia tool for adjusting specific options.
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
[/b]

save and exit.
Now it should appear in applications ---> System Tools
If not do a **killall gnome-panel** in the terminal.

---

