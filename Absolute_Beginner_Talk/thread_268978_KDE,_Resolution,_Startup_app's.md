---
title: "KDE, Resolution, Startup app's"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-10-01
HI there,

Been using Gnome for six months now, switched to KDE yesterday. Damn there are a lot of buttons to press! :)

Well, I've pressed most buttons and now KDE does what I need it to do, except for 2 things:

1) How do I change the screen resolution in KDE
2) How can I set an app to start at startup in KDE
3) How do you do a Print Screen in KDE

I have searched the forum but "resolution" gives me way to many hits and the wiki aint's so clued up on KDE.

Thanks,

Rudolf

PS: What config file controls the resolution that ultimatly gets loaded - xorg.conf only does drivers right?

---

### Post by kspringer on 2006-10-01
Answer to "1":
  "K Menu", "System Settings", "Display".

Thought I knew the answer to the other two but I don't.
Sorry...

---

### Post by RudolfMDLT on 2006-10-02
The problem seems a little deeper. I have a friend running fedora and we went onto every menu and cranny in KDE, no where do I have a DISPLAY setting. Any one know how to fix this? ;)

---

### Post by Marsolin on 2006-10-02
Install the [KDE Guidance]("http://linuxappfinder.com/package/kde-guidance") program from the Ubuntu repositories. It adds the ability to change screen resolution and manage hard drives. After install you can access it by choosing System Settings from the KDE Menu. Display is in the Hardware section. There is a slider that you can use to set the resolution.

If it doesn't give you the resolution you want as an option then you need to select the Hardware tab and make sure your monitor is listed correctly.

If you leave a program open in KDE when you shutdown it will automatically restart the next time you boot.

For printing the screen I would use the [KSnapshot]("http://linuxappfinder.com/package/ksnapshot") program.

---

