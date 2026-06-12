---
title: "wma in xmms?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by mills on 2007-03-24
hi all, 
	having a problem trying to play wma files on xmms i've followed the following guides/threads 

[http://www.ubuntuforums.org/showthread.php?t=117768&highlight=xmms+wma](http://www.ubuntuforums.org/showthread.php?t=117768&highlight=xmms+wma)
[http://www.ubuntuforums.org/showthread.php?t=312024&highlight=xmms+wma](http://www.ubuntuforums.org/showthread.php?t=312024&highlight=xmms+wma)
[http://www.ubuntuforums.org/showthread.php?t=117768&highlight=xmms+wma](http://www.ubuntuforums.org/showthread.php?t=117768&highlight=xmms+wma)

and installed
gstreamer0.10-ffmpeg
xmms-mp4
xmms-mad
win32codecs
alien

I also downloaded xmms-wma-1.0.4-1.i386.rpm here [http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)

then tried
	sudo alien xmms-wma-1.0.4-1.i386.rpm
	sudo dpkg -i *.deb
but i get; 
	File "xmms-wma-1.0.4-1.i386.rpm" not found.
i extracted it to the tmp folder and i can see it in there via nautilus
so why cant the terminal see it?

isnt there a way to just tell xmms to recognise the w32 codecs i have installed?

the codecs were downloaded with automatix.

i know this topics been discussed before but i feel like iam going round in circles here and as you can guess from the been count iam a bit of a noob
any help is really appreciated.

---

### Post by goatboy78 on 2007-03-26
I don't know anything about xmms but if you don't have any luck try a program called vlc. It plays just about anything.

---

### Post by clickelliott on 2008-02-11
Simple way to get XMMS to play WMA files:

***DISABLE*** WMA plug-in, 

**ENABLE** mplayer plug-in.

Done!:guitar:

---

