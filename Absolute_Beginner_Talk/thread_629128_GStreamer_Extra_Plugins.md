---
title: "GStreamer Extra Plugins"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by YeeP on 2007-12-02
Every time I try to install this ugly pack so I can view files like wmv(s), I get a program conflict.  I have "Movie Player" installed, which I thought was the program, but I removed it and that has done nothing for me.  Any tips?

Thank you!

---

### Post by FuturePilot on 2007-12-02
Can you post the exact error?

---

### Post by YeeP on 2007-12-02
This is from Applications>Add/Remove:

Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.


Sorry for not posting that before...
:)

---

### Post by FuturePilot on 2007-12-02
Try installing it from Synaptic
System>Administration>Synaptic Package Manager
Search for gstreamer0.10-plugins-ugly. Then try to install it. It should remove the conflicting package(s)

---

### Post by Delslayer on 2008-02-04
I'm having the same problem but when I try to install it through Synaptic it tells me:

"The following packages have unresolvable dependencies. make sure that all required repositories are added and enabled in preferences.
gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable"

---

### Post by FuturePilot on 2008-02-04
Make sure you have all the repos enabled under System&#8594;Administration&#8594;Software Sources. Also unckeck the CD-ROM if it happens to be checked.

---

### Post by Delslayer on 2008-02-04
I'm sorry but I'm a little unsure of what you mean by repos.

---

### Post by FuturePilot on 2008-02-04
Go System&#8594;Administration&#8594;Software Sources and check the first four boxes. Uncheck the CD-ROM if it happens to be checked. Now go to the Updates tab and check the first two and optionally the fourth. Click Close and then Reload when prompted.

The repos are online repositories where all the software is that you can download and install through the various tools such as Synaptic, Add/Remove, apt-get, etc.

---

### Post by Delslayer on 2008-02-04
Oh alright, works perfectly now. thank you so much.

---

