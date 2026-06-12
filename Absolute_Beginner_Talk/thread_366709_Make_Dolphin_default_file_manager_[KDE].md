---
title: "Make Dolphin default file manager? [KDE]"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Lexyboy on 2007-02-21
Hi All,

Just installed Dolphin & it seems pretty nice for what I want (i.e doesn't take 10 seconds to load every time I want to look at my ~, and uncluttered).  Only problem is, I can't work out how to make it the default FM instead of konqeror.  The docs say:

> To make dolphin the default file manager for kde from the kde control centre open the File Associations section via KDE Components>File Associations.  If the user adds dolphin to the list of applications for the directory mime type and make it the first choice, then dolphin will become the default application to open any directory with.  The directory mime type can be found by expanding the inode section of Known Types.

To make dolphin the default file manager for the virtual directories kde creates e.g. system:/ then again in the File Associations section of the control centre expand the inode section of Known Types.  Under the system_directory mime type, add dolphin to the list of applications, however instead of choosing dolphin from the kmenu, type the following in to the text box at the top  dolphin %u The virtual directories created by kde will then be opened by dolphin as default

but there's no such menu in Kubuntu, only a few options (browser, email etc).

Anyone managed this?

Thanks,

Alex

---

### Post by true_friend on 2007-02-23
Right Click on any folder and choose Open With
In new Window Select Dolphin or Write it in Address bar above of all in this window Check the box below Remember This Application and u are done. All files folders will be open in it Virtual Folders i do not know how to configure for Dolphin more if u cannot find Check box mentioned then first go to Properties then Click on Edit File Type Icon in front of Folder type having Tool Pic on it and then add there in new window Dolphin give it priority and update system settings then repeat this process u will have Dophin Default FM.
Cheers

---

### Post by zekica on 2007-03-03
You should start **kcontrol** instead of **systemsettings** application that replaces the former in KUbuntu. To do this, just select Run Command... form K Menu and type **kcontrol**. You will find file associations module there.

If kcontrol is not installed (I'm not sure it is installed by default), you can easily install it from package manager.

---

### Post by ramjet_1953 on 2007-03-03
I know it's off topic, but for those of us that use GNOME, Dolphin works fine under GNOME, assuming you have the necessary minimum KDE files installed.

Regards,
Roger :cool:

---

