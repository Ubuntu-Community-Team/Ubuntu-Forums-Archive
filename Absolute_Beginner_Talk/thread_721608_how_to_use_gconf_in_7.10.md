---
title: "how to use gconf in 7.10"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by brdohman on 2008-03-11
I'm running ubuntu 7.10, and I'm wanting to configure one of the users using the options available in gconf, but I can't figure out how to get it running.  I checked, and I do have it installed, just can't figure out how to get it running.

Thanks

---

### Post by drs305 on 2008-03-11
I am not quite sure if I know what you are asking, but you can use gconf to set specific configurations. The following example sets nautilus to list view:
```
gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer "list_view"
```
You can learn more about gconf by typing 
```
man gconftool
```

You can see what settings may be changed, what type they are (boolean, string, etc), and set them via gui (or get the syntax for a command line entry) with 
```
gconf-editor
```

---

### Post by forrestcupp on 2008-03-11
gconf-editor is what you are looking for.

But it's almost as complicated as the registry in Windows.  There is a lot to sift through.  Just be careful that you know what you're doing.

---

### Post by glennric on 2008-03-11
> **forrestcupp said:**
> gconf-editor is what you are looking for.

But it's almost as complicated as the registry in Windows.  There is a lot to sift through.  Just be careful that you know what you're doing.

Oh come now.  gconf-editor is not nearly as complicated as the registry in windows.  For one thing I don't think there is anything past a depth of 4.  How many levels does the windows registry have?  10 or more perhaps?

---

### Post by Oldsoldier2003 on 2008-03-11
> **glennric said:**
> Oh come now.  gconf-editor is not nearly as complicated as the registry in windows.  For one thing I don't think there is anything past a depth of 4.  How many levels does the windows registry have?  10 or more perhaps?

g conf editor isn't that confusing, after all its just a shiny guification of a text editor. Sometimes you still have to hunt down the configs and edit them manually anyhow...

---

### Post by forrestcupp on 2008-03-11
> **glennric said:**
> Oh come now.  gconf-editor is not nearly as complicated as the registry in windows.  For one thing I don't think there is anything past a depth of 4.  How many levels does the windows registry have?  10 or more perhaps?

If you know enough to get around gconf-editor, the Windows registry really isn't that bad either.  My point is that gconf-editor isn't as user friendly as the settings in the control panel.  It's set up more like the registry.

---

### Post by glennric on 2008-03-11
> **forrestcupp said:**
> If you know enough to get around gconf-editor, the Windows registry really isn't that bad either.  My point is that gconf-editor isn't as user friendly as the settings in the control panel.  It's set up more like the registry.

This is true.  I just hate to hear comparisons to windows.  The gconf-editor is not something that most people never need to deal with.

---

