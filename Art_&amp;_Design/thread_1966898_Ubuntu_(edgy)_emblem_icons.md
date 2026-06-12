---
title: "Ubuntu (edgy) emblem icons"
date: 2012-04-27
forum: Art &amp; Design
---

### Post by Perfect Storm on 2012-04-27
Greetings,

I'm looking for the emblem icons which (I believe) was available in 6.06

It look like this;
[IMG]http://ubuntu.5.n6.nabble.com/attachment/387789/0/edgy_emblems.png[/IMG]

Are there anyone who still have these icons, I have searching through the web without luck.

---

### Post by Perfect Storm on 2012-04-27
found them: [http://open-source.ecchi.ca/projets/ubuntu/ubuntu-theme-archive/6.10edgy/](http://open-source.ecchi.ca/projets/ubuntu/ubuntu-theme-archive/6.10edgy/)

---

### Post by Cariboo1938 on 2012-05-08
Hello,
I recently installed UbuntuStudio12.04 and I was wondering in which package are the "Emblems" I could use to decorate the Folder/Directory Icons :? 
> Index of /projets/ubuntu/ubuntu-theme-archive/6.10edgy
Parent Directory
edgy-gdm-themes_0.7-0ubuntu2_all.deb
edgy-session-splashes_0.4-0ubuntu1_all.deb
edgy-wallpapers_0.8-0ubuntu1_all.deb
gtk2-engines-ubuntulooks_0.9.12-2_i386.deb
human-cursors-theme_0.4-0ubuntu1_all.deb
human-icon-theme_0.7-0ubuntu1_all.deb
legacyhuman-theme_0.1-0ubuntu1_all.deb
Apache Server at open-source.ecchi.ca Port 80

---

### Post by Perfect Storm on 2012-05-08
human-icon-theme_0.7-0ubuntu1_all.deb

Extract it.

/usr/share/icons/human/scalable/emblems

You'll find all of them in .svg format so you can rescale them as you pleased.

---

### Post by Cariboo1938 on 2012-05-08
> **Artificial Intelligence said:**
> human-icon-theme_0.7-0ubuntu1_all.deb

Extract it.

/usr/share/icons/human/scalable/emblems

You'll find all of them in .svg format so you can rescale them as you pleased.

OK....Got it...Thank you!

But what I was actually up-to was [THIS]("http://library.gnome.org/users/user-guide/2.32/nautilus-emblems.html.en"). 
When I follow the instructions there, I have no option for "click on emblems". I guess my Ubuntu1204 installation is missing something!?

---

### Post by Perfect Storm on 2012-05-09
Nope, the Gnome3 devs have removed that option from nautilus. 

But there's a manual workaround: [http://www.webupd8.org/2011/12/how-to-manually-add-emblems-in-nautilus.html](http://www.webupd8.org/2011/12/how-to-manually-add-emblems-in-nautilus.html)

---

### Post by julio8a00 on 2012-05-09
awesome Icon pack!

---

### Post by Cariboo1938 on 2012-05-09
Thanks,
I could get back the "Emblems" option when right clicking file/folder. I could add emblems as I was used to. But I could not accomplish option a) from [HERE]("http://www.webupd8.org/2011/12/how-to-manually-add-emblems-in-nautilus.html") 
> 
4. If you want to add some more emblems, there are a few options available:
a) you can manually add emblem images under the ~/.icons/hicolor/48x48/emblems/ folder and they should automatically show up under Emblems > User (remember to restart Nautilus after this). This folder doesn't exist by default so create it firstly:
mkdir -p ~/.icons/hicolor/48x48/emblems

Here is a terminal output of the content of the newly created folder:
> 
[email]jg-laptop@JG-Laptop:~/.icons[/email]/hicolor/48x48/emblems$ ls -l
total 184
lrwxrwxrwx  1 jg-laptop jg-laptop    15 May  9 13:36 back.svg -> go-previous.svg
lrwxrwxrwx  1 jg-laptop jg-laptop    13 May  9 13:36 bottom.svg -> go-bottom.svg
-rw-r--r--  1 jg-laptop jg-laptop 89576 Mar 31  2010 calibrate.svg
lrwxrwxrwx  1 jg-laptop jg-laptop    11 May  9 13:36 down.svg -> go-down.svg
-rw-r--r--  1 jg-laptop jg-laptop  4443 May  9 13:31 edit-redo.svg
-rw-r--r--  1 jg-laptop jg-laptop  4146 May  9 13:31 edit-undo.svg
lrwxrwxrwx  1 jg-laptop jg-laptop    11 May  9 13:36 finish.svg -> go-last.svg
lrwxrwxrwx  1 jg-laptop jg-laptop    11 May  9 13:36 forward.svg -> go-next.svg
-rw-r--r--  1 jg-laptop jg-laptop  4417 May  9 13:31 go-bottom.svg
-rw-r--r--  1 jg-laptop jg-laptop  3130 May  9 13:31 go-down.svg
-rw-r--r--  1 jg-laptop jg-laptop  5102 May  9 13:31 go-first.svg
-rw-r--r--  1 jg-laptop jg-laptop  5489 May  9 13:31 go-home.svg
.
.
.
lrwxrwxrwx  1 jg-laptop jg-laptop    11 May  9 13:36 gohome.svg -> go-home.svg
-rw-r--r--  1 jg-laptop jg-laptop  5172 May  9 13:31 go-last.svg
-rw-r--r--  1 jg-laptop jg-laptop  3207 May  9 13:31 go-next.svg
-rw-r--r--  1 jg-laptop jg-laptop  3130 May  9 13:31 go-previous.svg
-rw-r--r--  1 jg-laptop jg-laptop  4119 May  9 13:31 go-top.svg
-rw-r--r--  1 jg-laptop jg-laptop  2863 May  9 13:31 go-up.svg
lrwxrwxrwx  1 jg-laptop jg-laptop    16 May  9 13:36 gtk-cancel.svg -> process-stop.svg
xrwxrwx  1 jg-laptop jg-laptop    16 May  9 13:36 reload.svg -> view-refresh.svg
[email]jg-laptop@JG-Laptop:~/.icons[/email]/hicolor/48x48/emblems$

And this shows that "python-nautilus" is installed:
> jg-laptop@JG-Laptop:~/.icons/hicolor/48x48/emblems$ cd /usr/share/nautilus-python/extensions/
jg-laptop@JG-Laptop:/usr/share/nautilus-python/extensions$ ls -l
total 20
-rw-rw-r-- 1 root root 4990 May  9 12:52 nautilus_emblems_menu.py
-rw-rw-r-- 1 root root 4982 May  9 12:45 nautilus_emblems_menu.py~
-rw-r--r-- 1 root root 3989 May  9 13:00 nautilus_emblems_menu.pyc
jg-laptop@JG-Laptop:/usr/share/nautilus-python/extensions$ 

The User option does not appear in the pulldown menu: see screenshot
And I do not quite understand how to add other Emblem folders.
Can somebody tell me what I missed to do, please?

---

### Post by Tux.tn on 2013-01-15
> **Cariboo1938 said:**
> 

The User option does not appear in the pulldown menu: see screenshot


Hi Cariboo1938,


Same for me, did you fix it ?

I've installed python-nautilus and created the * ~/.icons/hicolor/48x48/emblems *   user's emblems folder.



**Ubuntu 12.04 LTS.**

---

