---
title: "Edit Menus"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-16
When I select "Edit Menus" 

It says "Starting Applications Menu Editor" then does nothing.

How can I get this to work?

---

### Post by Perfect Storm on 2006-03-16
Try with:
```
smeg
```
and see what it says.

---

### Post by _simon_ on 2006-03-16
```

simon@ubuntu:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init_ _
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNot OnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNot OnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntr ies
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __ini t__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse
    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 30, in parse
    for line in file(filename,'r'):
IOError: [Errno 13] Permission denied: '/usr/share/applications/nvidia-settings. desktop'
simon@ubuntu:~$

```

---

### Post by Perfect Storm on 2006-03-16
Seems a permission setting of nvidia are crunching smeg. Also the space between the . and desktop.

```
cd /usr/share/applications
sudo rm -r nvidia-settings.$desktop
sudo gedit /usr/share/applications/nvidiasettings.desktop

```

add:

>  [Desktop Entry]
Name=Nvidia Control Center
Comment=Nvidia application
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;


---

### Post by _simon_ on 2006-03-16
if i do ls then it's displayed as "nvidia-settings.desktop"

The . is in the right place... ?

This is the current code:

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=/usr/share/pixmaps/nvsphere2.png
Terminal=false
Type=Application
Categories=Application;System;

```

Also I don't actually have a menu item for this!

---

### Post by Perfect Storm on 2006-03-16
Then change **sudo rm -r nvidia-settings.$desktop** to **sudo rm -r nvidia-settings.desktop**

It's because thte permission is wrong that you can't see it.

---

### Post by _simon_ on 2006-03-16
ah i see now.

Thank you, that's worked :)

---

