---
title: "Starting xscreensaver on boot/login in KDE"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by DonQuixote on 2006-02-27
How would I start xscreensaver automatically when starting KDE?  It starts fine in Gnome, but I have to start it manually in KDE when the prompt tells me it is not started.

Thanks!

---

### Post by patrick295767 on 2006-02-27
[QUOTE=DonQuixote]How would I start xscreensaver automatically when starting KDE?  It starts fine in Gnome, but I have to start it manually in KDE when the prompt tells me it is not started.

Thanks![/QUOTE]
maybe ... [http://www.ubuntuforums.org/showthread.php?t=104832&highlight=screensaver](http://www.ubuntuforums.org/showthread.php?t=104832&highlight=screensaver)


maybe
> I use a kcontrol module called Autostart, which starts programs up when you login to KDE.

The source code is found at [http://autostart.pwsp.net/](http://autostart.pwsp.net/)

Just download it to your disk, then unzip it with
Code:

tar xvjf autostart-0.2.tar.bz2 cd autostart-0.2 ./configure make make install


Make sure you have the Kde dev libraries installed, i.e. kde-devel

If you just want the binary, I've compiled a deb file of it below:

[http://www.drivehq.com/file/df.aspx/...0.2-1_i386.deb](http://www.drivehq.com/file/df.aspx/...0.2-1_i386.deb)
  
see ya'

---

### Post by DonQuixote on 2006-02-27
Thanks Patrick,

Is there a manual way to do it?  An entry in the init.d dir, a configuration change,  or something like that?

---

### Post by Stinger on 2006-02-28
Long time ago when I still used KDE I found [This guide on KDE-look]("http://www.kde-look.org/content/show.php?content=5319") , it worked flawlessly for me.
:)

---

### Post by DonQuixote on 2006-02-28
Thanks!

---

