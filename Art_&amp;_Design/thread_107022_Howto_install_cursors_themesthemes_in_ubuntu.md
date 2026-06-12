---
title: "Howto install cursors themes/themes in ubuntu"
date: 2005-12-22
forum: Art &amp; Design
---

### Post by ShirishAg75 on 2005-12-22
Hi all,
     Using ubuntu & gnome as my permanent window manager I wanna install some themes or at the very least a cursor theme. I looked all over gnome-look.org especially in the gnome cursor themes but there are no instructions how to install these. I know these are compressed files but beyond that haven't looked unless I know how to go about doing stuff.

---

### Post by Juippisi on 2005-12-22
Hmm, I'm not sure about Gnome, but try this:

cd ~
wget [http://your.cursor.com/theme.tar.gz](http://your.cursor.com/theme.tar.gz)
tar -xzvf theme.tar.gz
mkdir -p .icons/default
mv theme .icons/default

and restart Gnome. Should work!

Basically: Download, extract and move under .icons/default and restart app/Desktop Environment.

---

### Post by codejunkie on 2005-12-22
you could just install gcursor with
```
sudo apt-get install gcursor
```
and when you want to install a theme you just fireup gcursor and choose the theme and click install.

---

### Post by varunus on 2005-12-22
Gnome itself actually has cursor theme switching in System->Preferences->Mouse.

To install cursor themes, download the .tar.gz file somewhere, open up System->Preferences->Theme, click install theme, and point it at the cursor theme tar.gz file.  It will tell you that the icon theme was installed, this is really your cursor theme.  Then close the theme selector (don't click "Theme Details" and pick your cursor set, it won't work).

To select cursor themes, open up System->Preferences->Mouse and choose them from there.

---

### Post by ShirishAg75 on 2005-12-22
Opps blooper, I actually should've thanked codejunkie before only as my issue was solved by his gcursor thing. Although its handy to know this other way also varunas. Atleast have got a nice cursor theme.

---

### Post by Tiede on 2005-12-30
Just dropping in to say that this way (That I used to do before, did not work on my newly installed Breezy - Don't know why/don't ask) . It just shows a message telling the user that the file is in the wrong format...
The gcursor way and the manual $HOME/.icons way both work flawlessly though.

EDIT: THe way that does not work is the system->preferences->mouse way; The wrong format message comes from trying to drop it in System->preferences->Themes, which used to work (buggidh way of doing it)...

Reason for edit-->Precision

---

### Post by mattbarlow on 2006-01-10
[QUOTE=codejunkie]you could just install gcursor with
```
sudo apt-get install gcursor
```
and when you want to install a theme you just fireup gcursor and choose the theme and click install.[/QUOTE]

does it need to restart the x server after the installation of the theme?
the themes are added to the ./icons folder but they are not displayed in th gcursor?

---

### Post by Perfect Storm on 2006-01-10
I think I log out and a log in is enough.

---

