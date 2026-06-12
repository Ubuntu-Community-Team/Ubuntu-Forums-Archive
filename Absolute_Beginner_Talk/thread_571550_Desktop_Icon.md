---
title: "Desktop Icon"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by LaDeDa on 2007-10-09
I uninstalled "Sound Juicer" through the Synaptic Package Manager.   However, each time I insert a CD/DVD, the "Audio Disc"  icon appears on the desktop.  Irritating to say the least.  
How can I get rid of the icon permanantly  ??   TIA

---

### Post by strabes on 2007-10-09
In gnome, you can only disable **all** mounted media from appearing on the desktop. You can't pick and choose which types you want. (CDs, flash drives, etc.) If you would like to do this, press ALT+F2, run "gconf-editor" and browse to apps/nautilus/desktop. Uncheck "volumes_visible." The CD/volume icons on your desktop should immediately disappear.

By the way, why did you uninstall sound juicer? If you upgrade to the next version of ubuntu, you'll need to reinstall both the sound-juicer and ubuntu-desktop packages.

---

### Post by forestpixie on 2007-10-09
go to system preferences and then removable drives and media - you can turn off play a cd in there

---

### Post by LaDeDa on 2007-10-09
I've always like VLC.  When I insert a CD/DVD, bring up VLC to open it, all of a sudden "Sound Juicer" pops up, and along with it, the desktop icon.  I have another Win system with "Nero" which has always worked perfectly for me for burning media.  I uninstalled "Sound Juicer" simply because it ASSUMES I want to use it, when in fact, I don't.

---

### Post by forestpixie on 2007-10-09
so did you change the removable drives options ?

---

### Post by Forlong on 2007-10-09
You can set this the way you like in **System &#8594; Preferences &#8594; Removable Drives and Media &#8594; Multimedia &#8594; Audio CD Discs**

There's no need to take such actions as to remove an application, just because it pops up by default.

---

### Post by tech9 on 2007-10-09
> **LaDeDa said:**
> I uninstalled "Sound Juicer" through the Synaptic Package Manager.   However, each time I insert a CD/DVD, the "Audio Disc"  icon appears on the desktop.  Irritating to say the least.  
How can I get rid of the icon permanantly  ??   TIA

using gconf-editor" and browsing to apps/nautilus/desktop is your best bet

---

### Post by LaDeDa on 2007-10-09
I did use the gconf-editor and it worked perfectly.  Thanks for all the input.

---

