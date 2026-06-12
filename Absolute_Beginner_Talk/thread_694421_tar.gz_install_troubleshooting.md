---
title: "tar.gz install troubleshooting"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by smartygoldenfish on 2008-02-12
I downloaded a tar.gz file of Dark Theme for ubuntu.
[[http://www.gnome-look.org/content/show.php?content=32768]](http://www.gnome-look.org/content/show.php?content=32768])
i have ubuntu 7.10 on my VMPlayer with 768 MB RAM (windows xp=host)
I created a user(when asked in installation named Prateek and set its password)

What is bothering me is how to install this file.
I extract it and open specified directory in terminal.
But when i type **./configure** it says that[B]
bash: ./configure: No such file or directory[/B]

I said ok and typed [B]sudo make install
make: *** No rule to make target `install'.  Stop.
[/B]
that caused a lot of heart burn.
sudo checkinstall said this command is not found!!
Please Help!

---

### Post by kpkeerthi on 2008-02-12
You probably downloaded a theme. Open System -> Preference -> Appearance, then drag and drop the archive to into the dialog or click on the install button and choose the archive.

---

### Post by banewman on 2008-02-12
You don't unpack the theme  - go to system - preferences - themes in the menu and selact to install new theme then browse to the tat.gz and it will be installed.
:)

---

### Post by Tenken on 2008-02-12
Theme files don't need to be compiled, open System->Preferences->Appearnce and in the theme tab drag and drop the [i]darktheme[/].tar.gz file into the window.

---

