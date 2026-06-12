---
title: "Systemfile Permissions Denied"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Conquestor1 on 2007-11-08
I need to edit several system files. I am able to change the text, but when I try to save the text I get "Permissions Denied". I have read and understand how to change Permissions pursuant to 6.616.1 "Changing Permissions for a File". This seems to a root operation. I don't know or am unable to find a text resource that explains how to give myself this permission. Can anyone advise me.

I need to edit /etc/sane.d/dll.conf. I need to change epson to read epkowa.
I also need to add scanner specifics to /etc/udev/rules.d/45-libsane.rules.

---

### Post by Maestro23 on 2007-11-08
When editing/changing files owned by** / root**, you need to use the **sudo** command.  So if you want to use gedit to edit a system file:

> gkuso gedit .....

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gn2 on 2007-11-08
Press Alt+F2 and enter sudo nautilus

You will now have complete write access to all your system files, so go carefully.....

---

