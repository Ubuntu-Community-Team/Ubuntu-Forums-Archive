---
title: "Mouse Scroll Problem"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by xunshirine on 2006-11-17
Hi. I try Ubuntu 6.10 as a vmware guest on xp sp2 host. After installing vmware tools the mouse scroll button became inactivated. 
A possible solution ;

> In order to get the scroll wheel to work again after the above install, you will need to make a minor change to the xorg.conf file.

In the “Configured Mouse” section, change the following line as indicated:

Options “Protocol” “imps/2&#8243;

If you have more than five buttons (scroll wheel counts as three), then you might need the following line:

Options “Protocol” “ExplorerPS/2&#8243; 

But the problem is where is the ''Configured Mouse'' section and how the changes performed. Thanks

---

### Post by dante.regis on 2006-11-22
Hey there!

Sorry it took so much to anybody answer to you.

This section is inside the file xorg.conf . Follow these instructions:

Open a terminal and type this command

```

$ sudo gedit /etc/X11/xorg.conf
```
(It may ask you for a password. It's the one you use to login)

On the editor that opens, search for the section "Configured Mouse" as your solution tips us and then replace the section. My xorg.conf, particularly got only "ps/2", and even then I changed it to "ExplorerPS/2" (It worked with me, by the way :) Ubuntu 6.10 on VMWare Workstation 5.5.2)

Save the file and restart X

How to restart X? Simple. X (your graphic interface system) is restarted with Ctrl + Alt + Backspace. Rememeber to close any open programs so you don't loose your work. You'll have to login again.


Best
Dante

---

### Post by xunshirine on 2006-11-27
Thank you very much @Dante for the reply, it absolutely worked.

---

### Post by dm6257 on 2007-12-16
I installed Ubuntu 7.10 as a guest on VMWare running on XP p2.  I followed the instructions from VMWare to replace the "Configured Mouse" section in xorg.conf with  a "Mouse[0]" that uses a vmmouse  driver. Now the mouse releases nicely when I move from the VMWare window to the XP window.

But I have lost the scroll and the Mouse[0] section doesn't have a PS2 option.

Has anyone solved this problem?

dm6257

---

