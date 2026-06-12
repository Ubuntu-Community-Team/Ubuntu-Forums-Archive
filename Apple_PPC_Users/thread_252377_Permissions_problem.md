---
title: "Permissions problem"
date: 2006-09-06
forum: Apple PPC Users
---

### Post by nezermundy on 2006-09-06
Hello,

I have installed Ubuntu by using Parallels but have hit a problem, the screen resolution is wrong because the highest one is 1024x768 however I want it to be 1280x800. So on the Parallels forum they tell you how to do this, but this is where I hit the problem I have the new etc/X11/xorg.conf file, but I cannot edit or replace the file because I do not have permission to do this, I have tried changing my account etc but it does not work, the permissions, the file owner is root, if this helps.

Thank You,

Neil

---

### Post by chippy99 on 2006-09-06
Don't know what parallels is but presume since you post here you are using Ubuntu

In Ubuntu you normally type sudo before a command to gain root privileges. For example "sudo gedit /etc/X11/xorg.conf" which then ask you for a password and you enter the password for your own account. Note: This only applies to primary account you create at install, you have to change privs on other accounts created.

BTW in gnome you can change resolution from menu System -> Preference -> Screen Resolution

---

