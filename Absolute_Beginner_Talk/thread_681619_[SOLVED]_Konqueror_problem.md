---
title: "[SOLVED] Konqueror problem"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by malty on 2008-01-29
The following problem in Konqueror is intermittent, sometimes not happening for days and then is constantly there.
 Only in Konquerors web browser, not in the file browser...
 
 KDE crash handler..
 The application, unknown (NS plugin viewer), crashed & caused Signal 11 (SIGSEGU).
 
 In the backtrace window ...."this backtrace appears to be of no use" .
 
 The odd thing is there is nothing wrong, the webpages are fine.
 Viewing is normal, nothing is blocked or not appearing.
 
 The only other thing is, is that copy is strange, only in Konqueror, holding down the mouse button alone will not work, slightly moving the mouse is also required to activate the copy context menu, not doing this jumps the webpage back one place I do not know if this is related.
                                                      Malty

---

### Post by tchoklat on 2008-01-29
is it because Konqueror is a KDE app not a Gnome app and may be missing some dependencies?

perhaps!

---

### Post by AlanR8 on 2008-01-29
Never seen that before in Konqueror and I've been using it now for over a year full time. However, I don't use it to browse the web, just as a file manager. Its far superior (IMHO) to Dolphin and one of the first things I do on a fresh install is make Konqueror the default application for file browsing.

I don't understand the remark about it being a KDE application therefore there may be some missing dependencies. I've installed Kubuntu on 10 machines over the last year all with different specs and not see the problem you're reporting.

Sorry I can't be of more help to you.

---

### Post by Whiffle on 2008-01-29
If i'm not mistaken, nspluginviewer is what allows it to use netscape plugins.  I get the same error from time to time, I think its usually when flash crashes.  You might try removing and reinstalling flash or trying a different version of flash.

---

### Post by Whiffle on 2008-01-29
I think I figured it out, the newest version of flash is incompatable with Konqueror.  You'll have to find an old version of it somewhere, I'll post one if I find it.

---

### Post by Whiffle on 2008-01-29
I found it and attached it.  To use it, uninstall any and all flash players you might have, untar this file, open it, and run the install program.  

```

tar zxvf install_flash_player_9r48_linux.tar.gz
cd install_flash_player_9_linux/
./flashplayer-installer

```

After it has installed, go to Konqueror > Settings > Configure Konqueror > Plugins > Scan.  After it has scanned, check in the plugins tab and make sure it found the version thats in your home directory ( mine is /home/andy/.mozilla/plugins/libflashplayer.so ) .  If it doesn't, you've still got another version on your system somewhere that you need to delete.

EDIT:  Oops, its too big to upload.  I put it up on my baby web server, please don't kill it.  

[http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz](http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz)

---

### Post by malty on 2008-01-31
Whiffle..thanks, it worked
                                            Regards
                                                             Malty

---

