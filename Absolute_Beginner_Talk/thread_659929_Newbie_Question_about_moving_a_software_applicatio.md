---
title: "Newbie Question about moving a software application"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by explorer716 on 2008-01-06
In error I installed RealPlayer  on my Desktop (/home/robert/Desktop/RealPlayer).  What  are the steps I need to take to move Realplayer from the Desktop to the correct location?

As you can tell my skill is low.

Thank you in advance for your help.

---

### Post by Daveth on 2008-01-06
are you sure it is not just a desktop configuration file? Will tell you in nautilis is you go to /home/robert/desktop

---

### Post by explorer716 on 2008-01-06
It is not a desktop configuration file.  When I try to just delete it I get this message:
  Cannot move "/home/rober...RealPlayer" to the trash because you do not have permissions to change it or its parent folder.

---

### Post by Daveth on 2008-01-06
an inelegant way is through

```
gksudo nautilus
```

which opens up nautilus in superuser mode, giving you godlike powers- so beware!
I think you should actually bin that copy and install afresh- i'm not sure what happens to linux progs if you move parts of them from where they were installed, or whether symlinks etc follow on. 
Perhaps someone here will tell us both??

---

### Post by ajgreeny on 2008-01-06
How on earth did you install it in the first place, and how did you manage to install it on to the desktop?  If you had used either dpkg or apt it would have installed in the right place, so I presume you must have done it manually from a downloaded archive; not the easiest way to install things in Ubuntu.

---

### Post by Daveth on 2008-01-06
yes, quite a task to stick it on the desktop. This will be worth looking at

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

---

### Post by thelatinist on 2008-01-06
Are you sure you actually installed it there?  Perhaps you just downloaded or extracted an archive to that location?  That wouldn't mean it was actually intalled there.  Please tell us the precise steps you took that created this RealPlayer folder on your desktop.

---

### Post by explorer716 on 2008-01-06
Frankly I don't know How I installed it.  I am sure that it is installed because I can go to Applications> Sounds&Video> RealPlayer10 and double click to open RealPlayer10.

At this point all I want to do is remove the application from my Desktop.

---

### Post by ajgreeny on 2008-01-06
I'm still baffled!  Right click on the desktop item and chose "Properties" and tell us what it says in the line which starts "Type".  If it is a folder, open it and see what is in it.  If it's a file, is it "executable"?
Very strange.  I repeat, how did you install it?  With synaptic or apt-get, or did you download a tarball from the realplayer website?

---

### Post by explorer716 on 2008-01-06
As you requested I clicked on the desktop item and chose properties.  The type is "Folder".

---

### Post by thelatinist on 2008-01-06
If you really want to move that folder, it is possible to move it as root.  But first we should really find out what's going on.  I think it's possible that RealPlayer is actually installed somewhere else and that this folder is just a temp folder used when installing.

First:

1) Right-click on Applications and choose "Edit Menus."
2) In the left pane of the resulting window, click on "Sound & Video."
3) Find RealPlayer10 in the Right pane, left click on it, and choose "Properties."

What does it say under "Command"?

Second:

Open Nautilus and look in /usr/bin/ and /usr/local/bin/ for a file called something like "RealPlayer" or "RealPlayer10" or something similar.  Right-click on it and check the type.  What is it?

Third:

Open the folder "RealPlayer10" on your desktop.  What files and folders are in it?

---

