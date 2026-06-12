---
title: "[SOLVED] MS Office 2003 Wine Problems"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by bconverse on 2007-11-09
O

---

### Post by bconverse on 2007-11-09
Ok, so I posted before I was finished typing by accident.  But, anyways, I (stupidly) tried to install MS Office 2003 in Wine last night, just to experiment. At first, all seemed to be going well. The program installed and appeared in the wine applications menu.  However, whenever you try to run one of the applications, it will open, but immediately after a popup will appear saying "this application was not installed for this user, please run the installation again."  So I tried, and not change.  It won't uninstall now. I've tried uninstalling Wine in its entirety, but even if I do that, the Office apps still remain.  Is there any way to completely wipe this out? (Last time I ever try experimenting without reading further)

Thanks.

---

### Post by carlosjuero on 2007-11-09
> **bconverse said:**
> Ok, so I posted before I was finished typing by accident.  But, anyways, I (stupidly) tried to install MS Office 2003 in Wine last night, just to experiment. At first, all seemed to be going well. The program installed and appeared in the wine applications menu.  However, whenever you try to run one of the applications, it will open, but immediately after a popup will appear saying "this application was not installed for this user, please run the installation again."  So I tried, and not change.  It won't uninstall now. I've tried uninstalling Wine in its entirety, but even if I do that, the Office apps still remain.  Is there any way to completely wipe this out? (Last time I ever try experimenting without reading further)

Thanks.
The WINE C: drive is located at ~/.wine/c_drive

That is where all of the files for Office (and other emulated stuff) will be installed. When you remove WINE, you don't remove that folder as it acts as 'preferences' for the emulation engine. If you just want to get rid of office, go into ~/.wine/c_drive/Program Files/ and delete the Microsoft Office folder.

---

### Post by bconverse on 2007-11-09
Ok, thats what I thought.  Just wanted to make sure there were no further steps to take.  Thanks!

---

### Post by carlosjuero on 2007-11-09
Yep that should be about it.

---

### Post by Mithrilhall on 2007-11-09
Did you try running 'uninstaller' or 'uninstall' (I can't remember which command it was) from a console?

---

### Post by bconverse on 2007-11-13
Ok, so I have managed to remove the attempt at an office install, it was still appearing in the Applications --->Wine---->Programs menu.  So, I tried uninstalling wine again to get rid of it. I completely removed it using synaptic.  However, now when I reinstall wine, it installs, but it does not appear in the applications menu where it used to.  I tried to add to the menu, and there is an option to add the "wine windows emulator" but, it is not the same menu that used to be there and it does nothing upon clicking after being added to the menu.  So, my question is, how do I get the entire Wine menu back into the normal place in the "Applications" menu.

Hopefully this is just a noob overlook of something obvious, but any help would still be appreciated.

---

### Post by Mithrilhall on 2007-11-14
I thought it didn't get added to the menu unless there was a program installed via wine (I could be wrong though).

---

### Post by bconverse on 2007-11-14
> **Mithrilhall said:**
> I thought it didn't get added to the menu unless there was a program installed via wine (I could be wrong though).

For me at least, it was added to the menu when I initially installed it.

---

