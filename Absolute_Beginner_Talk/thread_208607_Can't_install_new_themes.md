---
title: "Can't install new themes"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by nmehsr on 2006-07-03
I've tried downloading and installing various themes but i can't get any of them to work. Whenever i do i get a message telling me its an incorrect file type. I've also noticed that there are several different file types in each of the downloads. What file type should i select when prompted? not that i could get any of them to work...

---

### Post by atoponce on 2006-07-03
[quote=nmehsr]I've tried downloading and installing various themes but i can't get any of them to work. Whenever i do i get a message telling me its an incorrect file type. I've also noticed that there are several different file types in each of the downloads. What file type should i select when prompted? not that i could get any of them to work...[/quote]
Maybe you could be a little more specific.  What are the file types of the themes that you are downloading, where are you downloading them from and how are you trying to install them?

---

### Post by nmehsr on 2006-07-03
i'm downloading stuff from art.gnome.org. some of the files are just text with what looks like it could be css. some are xml and some called index.theme. I'm trying to install through system > preferences > Themes then going to install theme and trying the various files i just decompressed

---

### Post by atoponce on 2006-07-03
[quote=nmehsr]i'm downloading stuff from art.gnome.org. some of the files are just text with what looks like it could be css. some are xml and some called index.theme. I'm trying to install through system > preferences > Themes then going to install theme and trying the various files i just decompressed[/quote] I guess it depends on what you are trying to install.  Dowloading window borders are *.tar.gz, and install by selecting the *.tar.gz in the theme application.  Application themes are treated the same way.  So is everything else on the site, except for obviously background images.  So, are you unzipping and untaring the file?  You don't want to do that.

---

### Post by nmehsr on 2006-07-03
ah i see i was untarring them thanks

---

### Post by MaximB on 2006-07-04
it depends on what themes are you trying to install
if it's deksop or icons or taskbar...you should open the theme manager and go advanced then there are 3 tabs...drag your file (zipped) into the apropriate tab...that should do the work.

---

### Post by krazykirk on 2006-07-04
Just keep in mind that it's the easiest to to try to install the theme or whatever while it's still tarred.

---

### Post by vinodis on 2006-07-04
KDE themes were a pain to install. Gnome themes are easy to install. Just drag and drop. Compiling to get themes work is too tedious.

---

### Post by finite9 on 2006-07-04
I tried this but it doesn't work for me.  I downloaded a GDM theme from art.gnome.org and tried to drag the tar.gz into the theme manager: get invalid file type error.  I trird to install by clicking Install theme button, then browsing to the tar.gz, but same problem.  I tried downloading several differnt themes but all give same error.  Seems like bug in theme manager.  I use 6.06 LTS fresh install with latest updates on i386.  I tried starting theme manager with sudo from command line, but it gave errors and wouldn't start.

---

### Post by finite9 on 2006-07-13
I was doing it wrong!  dragging and dropping a tarball does work, but only if you drag it into the correct window!  There are different dialogues for GDM theme and wallpaper theme and I was dragging a GDM tarball into the wallpaper theme dialog.  Doh.

---

