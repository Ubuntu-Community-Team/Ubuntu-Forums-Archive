---
title: "A few Questions"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by ianaaji on 2006-07-29
I just installed Ubuntu a few days ago, and I'm still getting used to it, and I'm trying to keep my questions all together, so here they are.

1. Is there a way to get an "open terminal in this folder" option like Konqueror?

2. Is there a way to make shortcuts? If I want a way to open the / "folder" to look for something, is there a way to put that on my desktop?

3. Is there any way to turn a source file tarball into a .deb package? Or any package?

4. This is a bit longer, it's about my network connection. My set-up is this: My computer, dual-booting ubuntu dapper, and win xp pro SP2, another computer running Win XP home SP2. I have cable internet coming from a cable modem, which goes to our router, which goes to the two computers. Can I set up ubuntu to share files between the two computers? I have a network between them with xp. 

I think that's all, and thank you for your time :)

---

### Post by Theja on 2006-07-29
never tried it...I configured a keyboard shortcut alt+t for opening a terminal...:) it works well.
2nd question well you could place the folder on the desktop itself..anyway its in the home directory/partition ...
I have no idea abt the third....
share....obviously you can....with rdesktop you can do a remote login to the other WinXP SP2 m/c from this comp....and then ssh is always there....

Theja

---

### Post by croak77 on 2006-07-29
1. Install nautilus-open-terminal

2. In Nautilus you can bookmark places/folders. They will show up in your GNOME menu. Just drag the entry to the desktop to create a link.

---

### Post by sethmahoney on 2006-07-29
1.  Yes.  There are scripts for doing this floating around the forum.  You should do a search for "open terminal here" or something like that.

2.  Right-click on the folder and click "make link", then drag the new file to your desktop.

3.  Yes, but its complicated.  There are some threads for doing that on this forum.  As for turning other packages into .deb packages, try alien.

4.  Yes.  Check out samba.

---

