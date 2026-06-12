---
title: "[SOLVED] No desktop effects option"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by the.dark.lord on 2007-11-02
I just upgraded to Gutsy yesterday (64 bit), and there is no Desktop Effects option in the menu, I checked in the Main Menu, but it's not there. CompizFusion does not seem to be working, if it's installed.

---

### Post by Inxsible on 2007-11-02
you have to first enable the restricted drivers. If you have, then you can enable Compiz Fusion by going to System>>Preferences>>Appearances and selecting 'Normal' or 'Extra' on the last tab(forgot the name- @work on a windows machine currently :( )

---

### Post by Vadi on 2007-11-02
It got moved ti System - Appearance - Appearance - Visual effects.

You also want to get the settings manager for compiz ([click]("apt:compizconfig-settings-manager")).

---

### Post by the.dark.lord on 2007-11-02
> **Inxsible said:**
> you have to first enable the restricted drivers. If you have, then you can enable Compiz Fusion by going to System>>Preferences>>Appearances and selecting 'Normal' or 'Extra' on the last tab(forgot the name- @work on a windows machine currently :( )

Thanks... Tried it now...

I've enabled Restricted Drivers.... The tab is 'Visual Effects'... it's set on "None". When I choose any other option, and error saying 'The Composite extension is not available' comes.

---

### Post by Inxsible on 2007-11-02
you might not have restarted X after enabling your restricted drivers.

---

### Post by the.dark.lord on 2007-11-02
> **Vadi said:**
> It got moved ti System - Appearance - Appearance - Visual effects.

You also want to get the settings manager for compiz ([click]("apt:compizconfig-settings-manager")).

Thanks... I already have the manager installed... compiz does not seem to be working

---

### Post by the.dark.lord on 2007-11-02
> **Inxsible said:**
> you might not have restarted X after enabling your restricted drivers.

you mean reboot? I have rebooted, and the status of my ATI Mobility Radeon X1600 in Restricted Drivers Management is "In Use."

---

### Post by Gold3n on 2007-11-02
For me it just says, "Desktop Effects Could Not Be Enabled" 

I think it may have to do with me using dual monitors. It won't enable any of the Visual Effects. I have my Restricted Drivers running for the nvidia GeForce Go 6800 on my XPS Gen2.

---

### Post by Inxsible on 2007-11-02
Check to see if your cards have been black listed. If so, you will have to manually remove them from the blacklist file.

---

### Post by the.dark.lord on 2007-11-03
> **Inxsible said:**
> Check to see if your cards have been black listed. If so, you will have to manually remove them from the blacklist file.

How do I do that, please?

---

### Post by the.dark.lord on 2007-11-04
Hello?

---

### Post by the.dark.lord on 2007-11-04
This might help all of you people...

A friend of mine suggested I try this command

```
echo SKIP_CHECKS=yes > .config/compiz/compiz-manager
```

That still doesn't work.

When I type 'compiz' in the terminal, I get:

```

sauron@Mordor:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:6708): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:6708): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
/usr/bin/compiz.real (core) - Fatal: No composite extension



```

---

### Post by Forlong on 2007-11-04
When using the proprietary (restricted) driver, you have to install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by Gold3n on 2007-11-05
> **Forlong said:**
> When using the proprietary (restricted) driver, you have to install Xgl:
```
sudo apt-get install xserver-xgl
```

You're the man now dog!

Works like a champ now, thanks!

:guitar: \\:D/

---

### Post by the.dark.lord on 2007-11-12
> **Forlong said:**
> When using the proprietary (restricted) driver, you have to install Xgl:
```
sudo apt-get install xserver-xgl
```


This works just superb!!!!!!!! Thanks a trillion :)

Wow. The effects are supercool!!!!!!1

---

