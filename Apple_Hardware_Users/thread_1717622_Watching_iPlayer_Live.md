---
title: "Watching iPlayer Live"
date: 2011-03-30
forum: Apple Hardware Users
---

### Post by conal on 2011-03-30
As some of you may know, streaming video on the linux powerPC platform is a problem without a proper implementation of flash.

Seems none of the scripts for downloading iPlayer programs are currently working for Linux power-PC. This partly due to the BBC changing the game, and partly due to unmet dependencies on power-pc with the latest scripts (correct me if I'm wrong). 

However I think I am close to getting the live streams working, by going to [www.iPhone.tvcatchup.com](www.iPhone.tvcatchup.com) and clicking on the links to the channels, then choosing to open the m3u8 file with GNOME Mplayer. It streams the channel for about half a minute then cuts out. 

Does anyone know how to keep this going?

Thanks in advance!

Conal

---

### Post by ajgreeny on 2011-03-30
Doesn't **get-iplayer** work on a ppc setup?  There is a new .deb package available for it at version 2.79.1, but I admit I have no knowledge of apple products old or new, so it could be that **get-iplayer** is useless on that platform.

Go to [https://launchpad.net/ubuntu/+source/get-iplayer/2.79-1/+buildjob/2157311](https://launchpad.net/ubuntu/+source/get-iplayer/2.79-1/+buildjob/2157311) to download the .deb and you can give it a try.  It should let you d/l the programs available and then watch them in your favourite media player.

---

### Post by conal on 2011-03-30
Thanks ajgreeney, I love get-iplayer and have been using it on my wife's laptop with Mr Bob's GUI wrapper: [http://sourceforge.net/projects/giplayer/files/]("http://sourceforge.net/projects/giplayer/files/")- but I ran into dependency issues with get-iplayer on the ppc setup.

EDIT: I now have get-iplayer working on power-pc in Debian Squeeze. Had to install ffmpeg and vlc to make use of the download options. Downloading in the iphone format allows me to play the programs on my 400Mhz G3 imac.

---

### Post by conal on 2011-03-30
I thought I had solved the problem when I found a python program to handle M3u8 video streams here: [http://www.kevincasey.org/?p=25]("http://www.kevincasey.org/?p=25")

It works a treat with some of the commercial channels at iphone.tvcatchup.com but sadly not for BBC News or Aljazeera, which yield messages like this: 

```
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
ERROR:root:http://84.234.23.222:1935/iphone/iphone_c4.sdp/playlist.m3u8?wowzasessionid=1532362463
ERROR:twisted:Unhandled Error
Traceback (most recent call last):
Failure: twisted.web.error.Error: 403 Forbidden

Traceback (most recent call last):
Failure: twisted.web.error.Error: 403 Forbidden
conal@conal-desktop:~$
```

However I did get to watch 'Red Dwarf' on 'Dave' and  so I guess I'm making progress!!

---

