---
title: "Titlebar disappears when running Compiz"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by TMcKSmith on 2008-04-17
I'm running Kubuntu (Gutsy) on a Dell Inspiron d620 w/ NVIDIA drivers.  I'm trying to get compiz up and running.  I installed these packages:

sudo apt-get install compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-settings-manager sexy-python

when I type compiz--replace I get this output:
thomass@thomass-laptop:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d7 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting kde-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32




It seems to run, but all of the titlebars/window bars all disappear.  How can I correct this problem?  Thanks.

---

### Post by neurostu on 2008-04-17
Under the advanced settings look for something like Window Decoration and make sure that it is turned on.

---

