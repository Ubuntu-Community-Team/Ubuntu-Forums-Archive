---
title: "Flash Player"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by chrispche on 2007-12-09
After installing Flash Player I get the following message.

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flush plugin is NOT installed.

Any ideas?

---

### Post by sourcemorph on 2007-12-09
md5sum mismatch indicates that the file u downloaded is corrupt and not working properly... download it again from a different source..

---

### Post by chrispche on 2007-12-09
I can't it can only come from macromedia's flash site. How do I resolve this. If I use Gnash it's very slow and can barely play the videos.

---

### Post by steven0451 on 2007-12-09
> **chrispche said:**
> I can't it can only come from macromedia's flash site. How do I resolve this. If I use Gnash it's very slow and can barely play the videos.

I had the same problem and this worked for me:

Right click -> Save file as... [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Close firefox and extract the tar.gz.

Terminal: sudo nautilus /usr/lib/firefox/plugins/
Paste the libflashplugin.so into here and close and try firefox.

Hope this works!

---

### Post by staticvoid on 2007-12-09
symlinking might be your problem...

oh and did you download flash when firefox told you to install it?

---

### Post by daradib on 2007-12-09
See [http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

---

