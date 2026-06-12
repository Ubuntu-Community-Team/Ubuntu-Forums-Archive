---
title: "CD/DVD mounting and rebooting"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by CCAT on 2006-11-12
Two problems.

1. I'll put a DVD or CD in and Ubuntu won't detect it.  If I reboot then it shows up on my desktop that something is there.  Do I have to forcefully mount it or something?

2. Is there a way to disable the SHIFT + BACKSPACE reboot?  I'm fine with the CRTL + SHIFT + Backspace method but I sometimes hit Shift + Backspace accidentally.  (I actually just did it, argh!)

Thanks.

---

### Post by aidanr on 2006-11-12
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

make sure your dvd drive looks like this in /etc/fstab

/dev/hdc    /media/cdrom0   udf,iso9660    user,noauto     0       0

replace hdc with whatever your drive is

---

### Post by CCAT on 2006-11-12
> **aidanr said:**
> xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

where am I suppose to put this? in /etc/fstab?

---

### Post by CCAT on 2006-11-12
> **aidanr said:**
> make sure your dvd drive looks like this in /etc/fstab

/dev/hdc    /media/cdrom0   udf,iso9660    user,noauto     0       0

replace hdc with whatever your drive is

that didn't help
:(

---

### Post by aidanr on 2006-11-12
> **CCAT said:**
> where am I suppose to put this? in /etc/fstab?
no, put it in your startup programs
```
sudo gedit /usr/local/bin/shiftbackspace
```
```
#!/bin/bash
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```
save and exit, go to
System->Preferences->Sessions->Startup Programs
hit "Add", type in "shiftbackspace", hit ok and close

---

### Post by aidanr on 2006-11-12
type in the terminal "gconf-editor" and browser to desktop->gnome->volume-manager and make sure "automount_drives" and "automount_media" are both checked

---

