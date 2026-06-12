---
title: "Why are apps running on startup?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by pdxuser on 2007-03-18
When I start a new session for a certain user, Xubuntu always loads Process Manager and The Gimp.  It used to always load Process Manager and Mousepad.  None of these programs are in my Autostarted Applications list (which is empty).  Is there another reason these apps might be running on startup?

---

### Post by Kobalt on 2007-03-18
Try to press Ctrl+H inside your /home folder and look for a startup script or file that might come from Gnome. Open it, to make sure, and if it contains Gimp and Process Manager then you found the guilty one :) 
I had the same prob on my girlfriend's laptop (with gaim)...

---

### Post by pdxuser on 2007-03-18
What might such a script be called?  There's nothing obvious in there, though there is a .gimp folder (as well as hidden folders for apps that don't run at startup).

---

