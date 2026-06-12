---
title: "cant make the cube to work anyomre"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-04-01
i restarted and now i cant make the cube any help

---

### Post by joshrobinson on 2008-04-01
do you have ccsm installed? you should go in there and check your cube settings

if you dont, run this command

```
sudo apt-get install compizconfig-settings-manager
```
then
```
ccsm
``` 
to open it

---

### Post by patchido on 2008-04-01
i do.. and all the preferences are set up .. i dont know why it isnt working

---

### Post by joshrobinson on 2008-04-01
on the bottom panel, in the right corner, does it show 4 workspaces?

---

### Post by patchido on 2008-04-01
only 1 but in the ccsm in the general options it says 4

---

### Post by joshrobinson on 2008-04-01
right click that 1 workspace, and go to preferences, then bump up the columns to 4, and click close
see if cube works now

---

### Post by patchido on 2008-04-01
it doesnt... it only makes a plane

---

### Post by patchido on 2008-04-01
ive just noticed... nothing from the ccsm is working

---

### Post by joshrobinson on 2008-04-01
maybe try reinstalling ccsm?
thats a weird issue

---

### Post by patchido on 2008-04-01
i did still the same

---

### Post by joshrobinson on 2008-04-01
read through this thread, sounds like you ran something as sudo and screwed up the permissions

[http://ubuntuforums.org/showthread.php?t=650393]("http://ubuntuforums.org/showthread.php?t=650393")

---

### Post by kbless7 on 2008-04-01
Have you started compiz fusion yet? If not press <alt>f2 and run

```
compiz
```

---

### Post by patchido on 2008-04-01
wont work

---

### Post by kbless7 on 2008-04-01
ok. run it in the terminal and post the output

---

### Post by patchido on 2008-04-01
pato@pato-laptop:~$ sudo chown -R $USER:$USER $HOME
[sudo] password for pato:
pato@pato-laptop:~$ chmod -R u+rwX $HOME
pato@pato-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Not a JPEG file: starts with 0x89 0x50
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x57 specified for 0x3e00009 (KNotify - ).
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2400020 (Archive Ma)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

---

