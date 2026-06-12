---
title: "VLC plays DVD in windows, but not linux.  No media player will play DVDs"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2007-07-28
OK, when I try to play a DVD in ubuntu I get

gxine - No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL
Read error from /dev/dvd

kaffeine - The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (///dev/hda)

No plugin found

Totem - Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it

Please install the necessary plugins and restart Totem to be able to play this media.

(clicking OK goes back to main screen, also I know I installed a load of codecs for it earlier today)

VLC does nothing when I tell it to play!  Strange, because it works under XP!

EDIT: data DVDs work fine

---

### Post by zerobinary on 2007-07-28
try reading the restricted thingie in ubuntu thing it might help

---

### Post by Vague on 2007-07-28
[https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)

I believe that's what zerobinary is talking about.  It should answer your question.  The "Playing DVDs" link is what you want, but I linked to the main Restricted Formats page in case you were curious about support for the rest of them as well.

---

### Post by jgrabham on 2007-07-28
Well libdvdcss2 is already installed

so I try the thing underneath and I get

james@james-desktop:~$ sudo apt-get install libdvdread3 libxine1-ffmpeg
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
libxine1-ffmpeg is already the newest version.
libxine1-ffmpeg set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Gremlinzzz on 2007-07-28
I use smplayer to play movie dvds it works good i have Feisty install not sure what you have because you metitioned xgine. but here it is. 
[http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php)
and heres the deb package i  installed  smplayer package (Qt3; without KDE support)

[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
:guitar:

---

### Post by jgrabham on 2007-07-28
> **Gremlinzzz said:**
> I use smplayer to play movie dvds it works good i have Feisty install not sure what you have because you metitioned xgine. but here it is. 
[http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php)
and heres the deb package i  installed  smplayer package (Qt3; without KDE support)

[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
:guitar:

Weird, just installed them, then reinserted the DVD, and it started in totem

---

### Post by rickdog on 2007-07-28
As a rule now, with every install I do, I just go straight to Medibuntu and Automatix2 and load all restricted codecs and then I can play any dvd in any player without hassle. Although, once I figured out at the last second that I needed to run a cleaning disk through a dvd burner, right before I was going to order another one. Whew, since then no problems! Late.

---

### Post by donut2790 on 2007-08-14
try this, worked for me

sudo sh /usr/share/doc/libdvdread3/install-css.sh

---

