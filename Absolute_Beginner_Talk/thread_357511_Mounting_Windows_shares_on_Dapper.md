---
title: "Mounting Windows shares on Dapper"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by lagomorph on 2007-02-09
I  use fstab entries to mount windows shares on my dapper machine.  This is very good as I can now access files on our windows machines.  However, the mounted shares appear on the desktop of the Dapper machine.  How do I prevent that? I would just like them to appear in the mount directory specified.  The lines I used in fstab was like:

//Windows IP Address/PRINTQ    /home/lagomorph/PDF/printq smbfs username=lagomorph,password=*******,uid=lagomorph,gid=lagomorph 0 0

Is there anything that I can do to prevent these shares from cluttering up my desktop?

---

### Post by optotron on 2007-02-09
Dapper... thats with KDE isn't it?
Anyways I don't remember excactly how its done but its a setting in KDE that lets you change stuff like that. In other words; there's nothing wrong with your fstab settings...

It's something whith show mounted volumes or something like that

---

### Post by dannyboy79 on 2007-02-09
no it's not (well dapper CAN have kde). dapper has nothing to do with it being either kde or gnome. dapper comes in 3 different window managers. XFCE, KDE, & GNOME. I am actually curious about this as well though. I just spent the last 30 minutes trying to find this setting and couldn't find it. i even scoured the gconf-editor. can anyone help me get rid of the icon on my desktop that states, Network Servers. I don;t want that shortcut on my desktop. I know how to create a launcher but I can't figure out how to get rid of 1 that is already there. I veen tried to drag it to the trash but it remains.

---

### Post by lagomorph on 2007-02-10
> **dannyboy79 said:**
> no it's not (well dapper CAN have kde). dapper has nothing to do with it being either kde or gnome. dapper comes in 3 different window managers. XFCE, KDE, & GNOME. I am actually curious about this as well though. I just spent the last 30 minutes trying to find this setting and couldn't find it. i even scoured the gconf-editor. can anyone help me get rid of the icon on my desktop that states, Network Servers. I don;t want that shortcut on my desktop. I know how to create a launcher but I can't figure out how to get rid of 1 that is already there. I veen tried to drag it to the trash but it remains.

I use the gnome desktop. Now, it maybe useful to have the icon appear when a cd is inserted or when a usb drive is inserted - but to have these shares appearing is quite untidy.  I don't think it affects the functionality of things, but Ubuntu has a nice clean look and I like to keep it that way.

---

