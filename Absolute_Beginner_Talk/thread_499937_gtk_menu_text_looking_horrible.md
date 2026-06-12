---
title: "gtk menu text looking horrible"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by applegrew on 2007-07-13
Hi below is a screenshot of GTK menu in XMMS. It looks horribly disfigured. How do I fix it. Also how do I choose a new look and feel for GTK. I am running Kubuntu. (I remember there was a theme selector for GTK in ubuntu but not here). Furthermore I have tried Use KDE them and Use Qt theme for GTK, but to no avail. Pls help!

Also it seems Firefox is using Gnome controls. E.g the the file 'save as' dialog looks just as it used to in Ubuntu (Genome) and not like the ones in KDE. How do I make Firefox use KDE controls???

---

### Post by Seisen on 2007-07-13
Have you tried this?

[http://www.freedesktop.org/wiki/Software/gtk-qt]("http://www.freedesktop.org/wiki/Software/gtk-qt")

---

### Post by applegrew on 2007-07-13
Maybe I should correct myself. Firefox too is using GTK as Gimp is using ?

---

### Post by applegrew on 2007-07-13
> **Seisen said:**
> Have you tried this?

[http://www.freedesktop.org/wiki/Software/gtk-qt]("http://www.freedesktop.org/wiki/Software/gtk-qt")

Yup Adept shows this is already installed.

---

### Post by Seisen on 2007-07-13
This website says something about qtcurve maybe that will fix your problem.

[http://liquidweather.net/howto/index.php?id=93]("http://liquidweather.net/howto/index.php?id=93")

---

### Post by applegrew on 2007-07-13
> **Seisen said:**
> This website says something about qtcurve maybe that will fix your problem.

[http://liquidweather.net/howto/index.php?id=93]("http://liquidweather.net/howto/index.php?id=93")
hey thnaks. I have tried that. That's why GIMP doesn't look so bad. The problem is with XMMS which uses GTK 1 and it ignores those settings. Currently I am reading the thread [http://ubuntuforums.org/showthread.php?t=107135](http://ubuntuforums.org/showthread.php?t=107135). It looks promising.

The another problem I want to fix related to firefox is how do I make it use KDE style Dialog boxes and not the GTK style one.

---

### Post by Seisen on 2007-07-13
Enter "about:config" in the address bar, look for the "ui.allow_platform_file_picker" key and change its value to "false". 

That should change the dialog box.

---

### Post by bonzodog on 2007-07-13
You won't get Firefox to use KDE widget themes unless you install the gtk-qt crossover engine (which is probably still installed). Firefox is built using GTK to draw it's widgets, so you won't be able to get it to look like KDE very much, unless you find a GTK theme that looks similar to the KDE one you are using (A good starting point might be gnome-look.org). 

As for XMMS, can I suggest you replace it with Audacious, as this now has all the same plugins and operability of XMMS but in gtk2-  in fact it can do things that Xmms can't, like reduce to the system tray, and it has a graphical track announcer, and can run 'headless', taking commands from a remote source.

If you are now using KDE for your desktop, you might like to try using Konqueror for your browser, as it is KDE native, and thus will follow the KDE theming, and it has plugins for things like Ad-blocking etc.

---

### Post by applegrew on 2007-07-13
@Seisen I used ur tip. The new dialog is not the KDE one, but it looks much better. Thanks! :)
@bonzodog I will right now check out Audacious. Thanks. :) The reason I wanted to use XMMS even when I have Amarok installed is that I wanted a feature where I can just tell the player to play files in any folder (including all the files in the sub folders).

---

### Post by petit.padavoine on 2007-07-13
You could also dodge your problem by dropping XMMS and using VLC. I don't know if it can play all the files in a folder recursively like you want though.

---

### Post by applegrew on 2007-07-13
> **bonzodog said:**
> You won't get Firefox to use KDE widget themes unless you install the gtk-qt crossover engine (which is probably still installed). Firefox is built using GTK to draw it's widgets, so you won't be able to get it to look like KDE very much, unless you find a GTK theme that looks similar to the KDE one you are using (A good starting point might be gnome-look.org). 

As for XMMS, can I suggest you replace it with Audacious, as this now has all the same plugins and operability of XMMS but in gtk2-  in fact it can do things that Xmms can't, like reduce to the system tray, and it has a graphical track announcer, and can run 'headless', taking commands from a remote source.

If you are now using KDE for your desktop, you might like to try using Konqueror for your browser, as it is KDE native, and thus will follow the KDE theming, and it has plugins for things like Ad-blocking etc.
Audacious looks quite sleek :). BTW how do I use the features u mentioned like reduce to the system tray, and it has a graphical track announcer, and can run 'headless'? I couldn't find any such options.

---

### Post by applegrew on 2007-07-13
> **petit.padavoine said:**
> You could also dodge your problem by dropping XMMS and using VLC. I don't know if it can play all the files in a folder recursively like you want though.
Yup but I find its Playlist uncomfortable to use.

---

### Post by applegrew on 2007-07-13
I have dumped xmms and now using Audacious. It does what I want. :)

---

