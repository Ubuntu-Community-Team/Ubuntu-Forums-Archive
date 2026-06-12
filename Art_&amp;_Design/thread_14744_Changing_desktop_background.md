---
title: "Changing desktop background"
date: 2005-02-09
forum: Art &amp; Design
---

### Post by mirtux on 2005-02-09
Hi,
   is there any possibility to find a program (maybe a deamon) that is capable of changing the desktop every fixed time, that can be set by the user?
 
 Thanks in advance,
 MC

---

### Post by gheorghe_pop on 2005-02-09
None that i know of.But you could easly build one and then share it with the comunity and maybe webshots.com will like it and then they will launch a background service for linux :wink:

---

### Post by Jad on 2005-02-09
is there a command line for changing the desktop background?

---

### Post by rwabel on 2005-02-09
[QUOTE=mirtux]Hi,
   is there any possibility to find a program (maybe a deamon) that is capable of changing the desktop every fixed time, that can be set by the user?
 
 Thanks in advance,
 MC[/QUOTE]

don't know this app, but maybe it's doing the job
[http://bgchanger.sourceforge.net/](http://bgchanger.sourceforge.net/)

---

### Post by bvc on 2005-02-09
[http://www.gnomefiles.org/app.php?soft_id=510](http://www.gnomefiles.org/app.php?soft_id=510)
[http://www.gnomefiles.org/app.php?soft_id=104](http://www.gnomefiles.org/app.php?soft_id=104)
[http://www.gnomefiles.org/app.php?soft_id=270](http://www.gnomefiles.org/app.php?soft_id=270)

chbg is in hoary
[http://sourceforge.net/projects/chbg/](http://sourceforge.net/projects/chbg/)
[http://freshmeat.net/projects/chbg/](http://freshmeat.net/projects/chbg/)
> A tool for changing the desktop background image in X11
A GTK+ based program that lets you periodically change your X
desktop.  It has several random effects, a slideshow, and
and may act as a xscreensaver hack or as a standalone screensaver.

Homepage: [http://chbg.sourceforge.net/](http://chbg.sourceforge.net/)

---

### Post by mirtux on 2005-02-10
Thanks everybody i've got it, that's what i was searching for!
 
 Regards,
 MC

---

### Post by Kat of Zion on 2007-01-27
> **rwabel said:**
> don't know this app, but maybe it's doing the job
[http://bgchanger.sourceforge.net/](http://bgchanger.sourceforge.net/)

There is one change that needs to be done before it can work properly with folder/file names that contain spaces. It was in the bgchanger.py located in the /usr/share/bgchanger/lib/ folder.  Simply change one line.

Old line:
cmd += "--set /desktop/gnome/background/picture_filename %s " % pic

New line:
cmd += "--set /desktop/gnome/background/picture_filename '%s' " % pic

It was literally that simple but it took me a bit to realize what was the program was doing in the code and my boyfriend to deduce how to change the code to reflect the solution. 

-Kat

---

### Post by KuriKai on 2007-01-28
[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

---

