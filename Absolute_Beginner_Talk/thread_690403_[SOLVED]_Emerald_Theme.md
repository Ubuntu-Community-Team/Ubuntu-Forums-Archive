---
title: "[SOLVED] Emerald Theme?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-07
[IMG]http://img530.imageshack.us/img530/2528/screenshotxd8.png[/IMG]

---

### Post by ~LoKe on 2008-02-07
Is there a question here?

**EDIT**: Oh, it's in the shot...

Anyways, the emerald theme handles window borders and titlebars. The rest is based on the GTK theme.

---

### Post by jordanmthomas on 2008-02-07
I believe he is saying he expected to be using a leopard compiz theme, which he is (though it looks more vistaish to me), but his gtk theme does not match.

---

### Post by billgoldberg on 2008-02-07
Ok.

First I think that's a vista emerald theme, but that's just me.

The transparent windows are called emerald.

To change the panels and the look and feel of the windows you need a [gtk 2 theme]("http://www.gnome-look.org/index.php?xcontentmode=100").

All of wich can be found on gnome-look.org

(there are packs that contain all the files (icons, gtk themes, emerald, gdm, ...)

like [URL="http://av.rds.yahoo.com/_ylt=A0Je5XfSRatHdOQAqTVrCqMX;_ylu=X3oDMTBvdmM3bGlxBHBndANhdl93ZWJfcmVzdWx0BHNlYwNzcg--/SIG=11rl8otum/EXP=1202493266/**http%3a//sourceforge.net/projects/mac4lin"]mac4lin
[/URL]
of [vistatransformation pack]("http://linuxowns.wordpress.com/2007/12/07/vista-transformation-pack/")

[the kore pack]("http://www.gnome-look.org/content/show.php/Kore-Gnome?content=55747")

....

---

### Post by blasteryui on 2008-02-07
Thank you kind sure now when I have a 2.x GTK that I want I save it to my desktop then how do I use it?

---

### Post by FuturePilot on 2008-02-07
System&#8594;Preferences&#8594;Appearance. Drag and drop the archive right into the window.

---

### Post by blasteryui on 2008-02-07
The GTK is a .zip and It says it's an invalid format when I try to "drag and drop"

---

### Post by Tenken on 2008-02-07
You can right click on the .zip file in your file browser and select "extract here", then depending on the file format you get from the newly extracted file you need to do different things:

If it's a .tar.gz you can drag and drop like suggested before

If it's a folder with no extentsion open a terminal and type

```
mv /path/to/GTK/theme ~/.themes
```

---

### Post by jordanmthomas on 2008-02-07
Ok, extract the zip file on your desktop.
If all that's left is a folder with the name of your theme, then do this:
 Press Alt + F2 and type
```
~/.themes
```
And move the folder in there.  If it says the location can't be found, then open your home directory and create a folder called .themes and then copy your theme in.


If there's more, as in some .tar.gz file(s), then, drag and drop them onto your theme preference window.

edit
err, what the guy above me said.  Too late :)

---

### Post by macogw on 2008-02-07
Have you drag n drop installed other stuff before?  If you have there will be a directory in your home drive called, I think, .themes (not sure, I don't have gnome on this computer).  If you go to View -> Hidden files and folders it should show in the file manager.  Just look at how the stuff is in there (I think it's just ~/.themes/theme1/ and ~/.themes/theme2/ etc), you can copy your unzipped theme into there and it should be added.

---

