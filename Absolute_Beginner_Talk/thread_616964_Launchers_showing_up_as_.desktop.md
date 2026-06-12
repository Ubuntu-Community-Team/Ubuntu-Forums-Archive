---
title: "Launchers showing up as *.desktop"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by pballgi on 2007-11-18
Whenever I try to use a launcher I have created I get an error window that says Cannot open *.desktop and has and error message. Ive attached an image.

---

### Post by pballgi on 2007-11-18
[http://ubuntuforums.org/showthread.php?p=3797339#post3797339]("http://ubuntuforums.org/showthread.php?p=3797339#post3797339")

---

### Post by ardchoille42 on 2007-11-18
> **pballgi said:**
> Whenever I try to use a launcher I have created I get an error window that says Cannot open *.desktop and has and error message. Ive attached an image.

All a launcher is is a .destop file which points to (Exec="blah") the desire app. The first thing I would look at are permissions of the launcher.

---

### Post by pballgi on 2007-11-18
I've tried to chmod +x it and such, but nothing seems to work.

---

### Post by pballgi on 2007-11-18
They worked fine originally, I just cant figure out what I could have possibly tweaked to do this.

---

### Post by zavius on 2007-11-21
I'm having the exact same problem. I can't figure out what I did to cause this. I'll let you know if I figure it out

---

### Post by stchman on 2007-11-21
> **pballgi said:**
> Whenever I try to use a launcher I have created I get an error window that says Cannot open *.desktop and has and error message. Ive attached an image.

.desktop files are supposed to be in the /usr/share/applications folder.

They are menu entries for Gnome.  Please post the output of your .desktop file here.  If it is good then copy it to your /usr/share/applications folder.

---

### Post by zavius on 2007-11-21
These desktop files where simply items added from the menu by right clicking and selecting "Add this launcher to desktop".

What could have changed for these not to launch applications? What program usually is associated with them?

---

