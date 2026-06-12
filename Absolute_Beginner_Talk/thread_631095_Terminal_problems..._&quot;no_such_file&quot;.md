---
title: "Terminal problems... &quot;no such file&quot;"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by lord.toan on 2007-12-04
I'm trying to install adobe flash on Ubuntu 7.10.  I had to do a workaround, so I read the instructions right up to where it tells me to perform 

> sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/

I get the error 

> mv: cannot stat `install_flash_player_9_linux/libflashplayer.so': No such file or directory

The file's there.  i'm looking at it as we speak.  I've even tried moving it to the desktop and just using sudo mv libflashplayer.so /usr/lib/firefox/plugins

Still says there's no such file... I'm gonna try restarting, but in case that doesn't help, can someone give me some help?


Or at least tell me how to get root access in File Browser?

---

### Post by JayFunGee on 2007-12-04
Of course you don't want to work with root access all the time, so be careful. To get root acces simply type: sudo nautilus
It will prompt you for your password and then start the file browser.

---

### Post by hyper_ch on 2007-12-04
why not doing the install directly through firefox? I was asked whether I want to install adobe flash or the other one when I first went with firefox on a flash enabled site.

---

### Post by lord.toan on 2007-12-04
I did the work around, put the .so file in firefox's folder with gksudo 

You're right, I wouldn't normally, but I dn't know why my terminal can't see files that are right in front of me.

It's still giving me a few problems with some of the online flash games on gaiaonline.  I dunno how exactly to fix that.  The game itself works, but it doesn't connect to online areas.

---

