---
title: "Problems with Epidermis: Cannot find installed pigment"
date: 2009-01-05
forum: Art &amp; Design
---

### Post by second.exodous on 2009-01-05
I didn't see a forum at the Epidermis site so I decided to post here, if anyone knows of somewhere better please direct me to there.

Anyway, I have two computers, one installed fine, got all 4 backages to work, but my other computer is having trouble.  I went to get all the themes and only two loaded, the default ubuntu them and Ubuntu Studio.  The two I don't want to use ironically, I like the OSX and mint themes better.

When I go to find more I get an error window 
'Error loading repo
An unexpected error occured: Cannot find installed pigment'

Anyone have any ideas?  One thing about the install on this computer is the install is in Portuguese, could that affect the install?

Thanx,
Stan

Edit:  Err, this doesn't seem to be a support forum, sorry, I posted in the wrong place, could one of the mods move it for me?

---

### Post by Orlsend on 2009-01-06
Hello Second Exodus.

Sadly We don't have a forum, but I think you posted in the rigth place.

I would like to troubleshoot your problem, First what Version of Epidermis are you using, and then what version Ubuntu are you using? are in 32bits or 64bits?

And If could copy and paste the error code or the error it self here that would be awesome.

I am only the website maintainer and translator of epidermis, but I ll make sure Flimm the code maintainer knows about this so we could get you favorite skins going :D!

---

### Post by second.exodous on 2009-01-06
Thanks for responding, I really like the ease to change Ubuntu's theme, which I don't like.

Ok, I'm using Epidermis .21, 8.10, 32 bit, and am running through Portugues.  I'm guessing it has something to do with how the folders are named, but I'll post my code below.


```
laptop:~$ epidermis 
Epidermis, Copyright (C) 2008 David D Lowe
Epidermis comes with ABSOLUTELY NO WARRANTY; for details click on the About button, License
This is free software, and you are welcome to redistribute it
under certain conditions; for details click on the About button, License
/usr/lib/python2.5/site-packages/epidermis/epidermis.py:301: GtkWarning: gdk_window_set_icon_list: icons too large
  self.win.show_all()
Cannot find installed pigment
Exception in thread DownloadRepoThread:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.5/site-packages/epidermis/loadrepo.py", line 256, in run
    self.run2()
  File "/usr/lib/python2.5/site-packages/epidermis/loadrepo.py", line 371, in run2
    load_cached_repo()
  File "/usr/lib/python2.5/site-packages/epidermis/loadrepo.py", line 149, in load_cached_repo
    raise(Exception("Cannot find installed pigment"))
Exception: Cannot find installed pigment
```

This is the last day I can trouble shoot until the September 20 as I'm going to Brazil tomorrow to give this notebook to a family there and they won't have internet until then.

One thing I should point out is I wanted to use the OSX theme and everything is there, I just have to modify one of the other themes to have all the OSX stuff.  If you need anything else just ask.

Thanx,
Stan

---

### Post by Orlsend on 2009-01-06
OK I am going to post the bug on list (Launchpad) and I am sure Flimm will get to it as he can,By reading on the bug report seems like what you been telling me, though Again my knowledge in python is very limited.

---

### Post by Flimm on 2009-01-07
Hi, I'm the develepor of [Epidermis](http://epidermis.tuxfamily.org).
I can't reproduce this bug on my machine, so could you help me debug it?
Could you post the output of this command:
ls -R ~/.local/share/epidermis

---

### Post by dentaku65 on 2009-01-17
> **Flimm said:**
> Hi, I'm the develepor of [Epidermis](http://epidermis.tuxfamily.org).
I can't reproduce this bug on my machine, so could you help me debug it?
Could you post the output of this command:
ls -R ~/.local/share/epidermis

I have the same issue of "pigment"
here is the output of:
ls -alR ~/.local/share/epidermis
btw after the first installation, I've found only 3 themes (Studio, Intrepid and Mint) the Mac one give an error during the last part of the 1st intallation (sorry I did not catch it); if I try Find More button, I get the pigment error message.

```
/home/zander/.local/share/epidermis:
total 48
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 .
drwx------  4 zander zander 4096 2009-01-17 08:27 ..
drwxr-xr-x  5 zander zander 4096 2009-01-17 08:49 cursors
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 gdm
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 gnomeSplashes
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 grub
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:47 gtk
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:48 icons
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:47 metacity
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 skins
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 usplashes
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:47 wallpapers

/home/zander/.local/share/epidermis/cursors:
total 20
drwxr-xr-x  5 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 ComixCursors-blue-regular
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 dmz-white
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 mac4lin

/home/zander/.local/share/epidermis/cursors/ComixCursors-blue-regular:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 5 zander zander 4096 2009-01-17 08:49 ..
-rwxr-xr-x 1 zander zander 1095 2009-01-17 08:49 mouse.png
-rw-r--r-- 1 zander zander  394 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/cursors/dmz-white:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 5 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander  815 2009-01-17 08:49 arrow.png
-rw-r--r-- 1 zander zander  342 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/cursors/mac4lin:
total 40
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:49 .
drwxr-xr-x 5 zander zander  4096 2009-01-17 08:49 ..
-rwxr-xr-x 1 zander zander 26450 2009-01-17 08:49 left_ptr.png
-rw-r--r-- 1 zander zander   330 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/gdm:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 blue-folder
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 human
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 mac4lin

/home/zander/.local/share/epidermis/gdm/blue-folder:
total 60
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander   516 2009-01-17 08:49 pigment.xml
-rwxr-xr-x 1 zander zander 48204 2009-01-17 08:49 screenshot.jpg

/home/zander/.local/share/epidermis/gdm/human:
total 32
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander   425 2009-01-17 08:49 pigment.xml
-rw-r--r-- 1 zander zander 18023 2009-01-17 08:49 screenshot.png

/home/zander/.local/share/epidermis/gdm/linux-mint:
total 44
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander   354 2009-01-17 08:49 pigment.xml
-rw-r--r-- 1 zander zander 30657 2009-01-17 08:49 screenshot.png

/home/zander/.local/share/epidermis/gdm/mac4lin:
total 20
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander  324 2009-01-17 08:49 pigment.xml
-rwxr-xr-x 1 zander zander 5163 2009-01-17 08:49 screenshot.jpg

/home/zander/.local/share/epidermis/gnomeSplashes:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:48 blue-ubuntu
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:48 mac4lin
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:48 ubuntu-elephant

/home/zander/.local/share/epidermis/gnomeSplashes/blue-ubuntu:
total 48
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:48 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rwxr-xr-x 1 zander zander 34173 2009-01-17 08:48 blue.png
-rw-r--r-- 1 zander zander   332 2009-01-17 08:48 pigment.xml

/home/zander/.local/share/epidermis/gnomeSplashes/linux-mint:
total 88
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander 73232 2009-01-17 08:49 linuxmint.png
-rw-r--r-- 1 zander zander   379 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/gnomeSplashes/mac4lin:
total 60
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:48 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander   323 2009-01-17 08:48 pigment.xml
-rwxr-xr-x 1 zander zander 48833 2009-01-17 08:48 splash2.jpg

/home/zander/.local/share/epidermis/gnomeSplashes/ubuntu-elephant:
total 52
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:48 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander   422 2009-01-17 08:48 pigment.xml
-rw-r--r-- 1 zander zander 37438 2009-01-17 08:48 preview.png

/home/zander/.local/share/epidermis/grub:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 debian-moreblue-swirl
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 mac4lin-dark
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 ubuntu-black

/home/zander/.local/share/epidermis/grub/debian-moreblue-swirl:
total 44
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rwxr-xr-x 1 zander zander 30041 2009-01-17 08:49 debian-moreblue-swirl.png
-rw-r--r-- 1 zander zander   427 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/grub/linux-mint:
total 44
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander 29106 2009-01-17 08:49 linuxmint.png
-rw-r--r-- 1 zander zander   398 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/grub/mac4lin-dark:
total 40
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:49 ..
-rwxr-xr-x 1 zander zander 25321 2009-01-17 08:49 mac08.png
-rw-r--r-- 1 zander zander   325 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/grub/ubuntu-black:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander  816 2009-01-17 08:49 pigment.xml
-rw-r--r-- 1 zander zander  384 2009-01-17 08:49 ubuntu-black.png

/home/zander/.local/share/epidermis/gtk:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 human
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 mac4lin
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 ubuntu-studio

/home/zander/.local/share/epidermis/gtk/human:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rwxr-xr-x 1 zander zander 2414 2009-01-17 08:47 human-gtk.png
-rw-r--r-- 1 zander zander  432 2009-01-17 08:47 pigment.xml

/home/zander/.local/share/epidermis/gtk/linux-mint:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rw-r--r-- 1 zander zander 2134 2009-01-17 08:47 controls.png
-rw-r--r-- 1 zander zander  361 2009-01-17 08:47 pigment.xml

/home/zander/.local/share/epidermis/gtk/mac4lin:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rw-r--r-- 1 zander zander  318 2009-01-17 08:47 pigment.xml
-rwxr-xr-x 1 zander zander 3278 2009-01-17 08:47 shot.png

/home/zander/.local/share/epidermis/gtk/ubuntu-studio:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rw-r--r-- 1 zander zander  396 2009-01-17 08:47 pigment.xml
-rwxr-xr-x 1 zander zander 2062 2009-01-17 08:47 preview.png

/home/zander/.local/share/epidermis/icons:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:48 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:48 human
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:48 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:48 mac4lin
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:48 ubuntu-studio

/home/zander/.local/share/epidermis/icons/human:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:48 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:48 ..
-rw-r--r-- 1 zander zander 3150 2009-01-17 08:48 folder.png
-rw-r--r-- 1 zander zander  404 2009-01-17 08:48 pigment.xml

/home/zander/.local/share/epidermis/icons/linux-mint:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:48 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:48 ..
-rw-r--r-- 1 zander zander 2549 2009-01-17 08:48 folder.svg
-rw-r--r-- 1 zander zander  348 2009-01-17 08:48 pigment.xml

/home/zander/.local/share/epidermis/icons/mac4lin:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:48 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:48 ..
-rwxr-xr-x 1 zander zander 2966 2009-01-17 08:48 Folder.png
-rw-r--r-- 1 zander zander  324 2009-01-17 08:48 pigment.xml

/home/zander/.local/share/epidermis/icons/ubuntu-studio:
total 68
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:48 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:48 ..
-rwxr-xr-x 1 zander zander 52062 2009-01-17 08:48 folder_new.svg
-rw-r--r-- 1 zander zander   403 2009-01-17 08:48 pigment.xml

/home/zander/.local/share/epidermis/metacity:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 human
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 mac4lin
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 ubuntu-studio

/home/zander/.local/share/epidermis/metacity/human:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rwxr-xr-x 1 zander zander 2448 2009-01-17 08:47 human-metacity.png
-rw-r--r-- 1 zander zander  442 2009-01-17 08:47 pigment.xml

/home/zander/.local/share/epidermis/metacity/linux-mint:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rw-r--r-- 1 zander zander 2144 2009-01-17 08:47 border.png
-rw-r--r-- 1 zander zander  369 2009-01-17 08:47 pigment.xml

/home/zander/.local/share/epidermis/metacity/mac4lin:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rw-r--r-- 1 zander zander  329 2009-01-17 08:47 pigment.xml
-rwxr-xr-x 1 zander zander 2695 2009-01-17 08:47 screenshot.png

/home/zander/.local/share/epidermis/metacity/ubuntu-studio:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rw-r--r-- 1 zander zander  401 2009-01-17 08:47 pigment.xml
-rwxr-xr-x 1 zander zander 2199 2009-01-17 08:47 preview.png

/home/zander/.local/share/epidermis/skins:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 mac4lin
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 ubuntu-intrepid-ibex
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 ubuntu-studio

/home/zander/.local/share/epidermis/skins/linux-mint:
total 12
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander 1089 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/skins/mac4lin:
total 12
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander 1231 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/skins/ubuntu-intrepid-ibex:
total 12
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander 1063 2009-01-17 08:49 pigment.xml

/home/zander/.local/share/epidermis/skins/ubuntu-studio:
total 8
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..

/home/zander/.local/share/epidermis/usplashes:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 mac4lin
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 splash
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:49 ubuntu

/home/zander/.local/share/epidermis/usplashes/linux-mint:
total 372
drwxr-xr-x 2 zander zander   4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander   4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander    431 2009-01-17 08:49 pigment.xml
-rw-r--r-- 1 zander zander 364305 2009-01-17 08:49 usplash.png

/home/zander/.local/share/epidermis/usplashes/mac4lin:
total 20
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander  334 2009-01-17 08:49 pigment.xml
-rwxr-xr-x 1 zander zander 7415 2009-01-17 08:49 screenshot.png

/home/zander/.local/share/epidermis/usplashes/splash:
total 20
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander  352 2009-01-17 08:49 pigment.xml
-rwxr-xr-x 1 zander zander 6172 2009-01-17 08:49 usplash.jpg

/home/zander/.local/share/epidermis/usplashes/ubuntu:
total 24
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:49 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:49 ..
-rw-r--r-- 1 zander zander  417 2009-01-17 08:49 pigment.xml
-rw-r--r-- 1 zander zander 9415 2009-01-17 08:49 usplash_640_480.png

/home/zander/.local/share/epidermis/wallpapers:
total 24
drwxr-xr-x  6 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 12 zander zander 4096 2009-01-17 08:28 ..
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 3lcd
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 human-intrepid-ibex
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 linux-mint
drwxr-xr-x  2 zander zander 4096 2009-01-17 08:47 mac4lin

/home/zander/.local/share/epidermis/wallpapers/3lcd:
total 32
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:47 ..
-rwxr-xr-x 1 zander zander 18046 2009-01-17 08:47 3lcd.png
-rw-r--r-- 1 zander zander   475 2009-01-17 08:47 pigment.xml

/home/zander/.local/share/epidermis/wallpapers/human-intrepid-ibex:
total 16
drwxr-xr-x 2 zander zander 4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander 4096 2009-01-17 08:47 ..
-rw-r--r-- 1 zander zander  682 2009-01-17 08:47 pigment.xml
-rw-r--r-- 1 zander zander 1718 2009-01-17 08:47 warty-final-ubuntu-prev.jpg

/home/zander/.local/share/epidermis/wallpapers/linux-mint:
total 24
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:47 ..
-rw-r--r-- 1 zander zander 12248 2009-01-17 08:47 LinuxMint_preview.png
-rw-r--r-- 1 zander zander   549 2009-01-17 08:47 pigment.xml

/home/zander/.local/share/epidermis/wallpapers/mac4lin:
total 100
drwxr-xr-x 2 zander zander  4096 2009-01-17 08:47 .
drwxr-xr-x 6 zander zander  4096 2009-01-17 08:47 ..
-rwxr-xr-x 1 zander zander 83774 2009-01-17 08:47 mac4lin.jpg
-rw-r--r-- 1 zander zander   478 2009-01-17 08:47 pigment.xml
```

---

### Post by Flimm on 2009-01-17
I've released a new version of Epidermis, 0.2.2, go get it [here](https://launchpad.net/epidermis/+download). This release doesn't fix this bug as far as I'm aware, but it should display more debugging information that should help me reproduce the problem.

---

### Post by dentaku65 on 2009-01-18
> **Flimm said:**
> I've released a new version of Epidermis, 0.2.2, go get it [here](https://launchpad.net/epidermis/+download). This release doesn't fix this bug as far as I'm aware, but it should display more debugging information that should help me reproduce the problem.

This version (0.2.2) works very well.
I remove the old profile 
```
rm -R ~/.local/share/epidermis
```
Then I re-download everything with this new version and now all the desktop themes are available and applicable

Thanks! :P

---

### Post by Flimm on 2009-01-18
> **dentaku65 said:**
> This version (0.2.2) works very well.
I remove the old profile 
```
rm -R ~/.local/share/epidermis
```
Then I re-download everything with this new version and now all the desktop themes are available and applicable

Thanks! :P
I'm very glad to hear that!
Unfortunately, since I don't know why this issue isn't occurring anymore, I still can't consider this bug as fixed. Maybe this problem has to do with the pigments, not Epidermis. If that's the case, could anyone who still seems to have this problem delete ~/.local/share/epidermis and try downloading the pigments again? I regularly update them.

---

### Post by rfreedman on 2009-04-24
I'm using version  0.21, that was installed when I upgraded to Jaunty.
I see this problem if I try to download all of the the themes at once.

I removed my ~/.local/share/epidermis directory, and this is very repeatable.

If I remove the directory, and then download the themes one at a time, it works fine.

---

