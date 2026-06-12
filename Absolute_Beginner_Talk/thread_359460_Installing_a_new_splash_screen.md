---
title: "Installing a new splash screen?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-12
Hi!  If I download a new splash screen from the Gnome website, what  do I do to install it? ^_^

---

### Post by fusiachi on 2007-02-12
Go to **Applications>System Tools>Configuration Editor**

If you don't have **System Tools** on your menu, go to **System>Preferences>Menu Layout** and add it.

From the config editor, go to **/apps/gnome-session/options/splash_image** and set the value to your new splash image's location.  

Restart X and it should work.  If not, well, someone else here certainly knows what they're talking about and can point you in the right direction.


Edit: The image should be a png.

---

### Post by Darklighter137 on 2007-02-12
Thanks for your reply, it was most helpful.   But, is there any special place that I need to put the new image for things to work smoothly?

---

### Post by fusiachi on 2007-02-12
> **Darklighter137 said:**
> Thanks for your reply, it was most helpful.   But, is there any special place that I need to put the new image for things to work smoothly?

What version are you running?  I'd put it in **/usr/share/pixmaps** to be sure (thought this might not be a necessity).  Let me know if it works.

---

### Post by Darklighter137 on 2007-02-12
I decided to place it in usr/share, but yes it did work.  Thanks! ^_^

---

