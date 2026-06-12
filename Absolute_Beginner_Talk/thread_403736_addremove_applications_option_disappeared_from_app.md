---
title: "add/remove applications option disappeared from applications menu in Xubuntu"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by tommie74 on 2007-04-07
Three days ago I installed Xubuntu on my laptop, so I am an absolute beginner. I don't know why, but when I installed Xubuntu there was a "add/remove applications" option in the Applications menu. I think this is more or less the same as Synaptic, or a different version of it. This option is missing now. Does anybody know howcome, and wether I can make it appear again? Has it something to do with upgrading all software in Synaptic?
Thx for looking,
Thomas de Graaff.

---

### Post by dstew on 2007-04-07
Do you have a menu entry for Synaptic? On my Xubuntu menu it is under Applications--->System. If so, just use that. I never had a menu entry for Add/Remove programs. I think Add/Remove programs is just an alias for Synaptic anyway.

By the way, do not try to edit your system menu using the Menu Editor. I have seen lots of posts about it not working properly, and people get their menus pretty messed up. There is a safe way to edit the menu, using a text editor from the command line in the terminal. See [http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/](http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/)

---

### Post by tommie74 on 2007-04-07
On my Xubuntu Synaptic is also under Apllications ---> System. If I remember correctly the add/remove applications option was under Applications ----> Others. It was the only option under Others. It was not the same as Synaptic. 
I've just found a thread about what appears to be the same program, only this is in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=399921&highlight=applications+menu+add](http://ubuntuforums.org/showthread.php?t=399921&highlight=applications+menu+add)

The program in Ubuntu is supposed to be in this location: /usr/bin/gnome-app-install
I've tried this in a terminal, but it doesn't exist. Maybe I've removed it using Synaptic or so... 

Thx for your advise about editing the menu! I am going to give this a look now!

---

### Post by tommie74 on 2007-04-07
I have installed /usr/bin/gnome-app-install using Synaptec. The add/remove application is not the same as Synaptec. It has a different vieuw, there is a panel with popularity which shows in stars how popular an application is, and a lot more. I've got it working now!
Thx again.

---

### Post by OsakaWilson on 2007-04-15
I got my add/remove back again by looking for "gnome-app-install" in Synaptic too. Thanks all.

---

