---
title: "How to fix the flash crash in firefox when you play videos on youtube."
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by zxccvb on 2007-09-05
I tried differents solutions proposed on this forum. None of them helped.

The set_ARGB_something placed almost anywhere didn't help a bit.
Disabling addon or even removing them: no use.
Installing Debian and using Iceweasel: waste of time.
etc etc

I finally solved this problem using the windows version of firefox with WINE.

This may be a *temporary *solution for you too until Adobe fix all the issues with their plugin. 
Or can be even a permanent one if like me you use the ImageZoom extension that doesn't work so well in the Linux version. 

I'm using it for a week now and the only crash i had was with the Java plugin.

Everything else just work. And I have tons of Addons too. 

Most important than everything else: Flash is stable as you can possibly wish.


I share what i did with you in case you are one of the unlucky guys that couldn't make any of thiose solution to actually work for you.

If you are interested in a step by step:

- Download firefox (WINDOWS version) from 
[http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)

- Install the last version of wine following these instructions
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

- in a console type:
  winecfg

In the "desktop integration" tab change the default colors of the Items. :)
The default dark gray really sucks! 
I suggest a lighter gray. Ivory perhaps. Just matter of taste i guess. But it's not Windows 98 anymore. :)

- in a console type
$ sudo aptitude install msttcorefonts

This will install the correct font otherwise you will se all the fonts rendered by firefox to be the same default Courier shitty like font. Trust me you want to install this.
(you may have to abilitate some repository to do this. if that's the case google aroud)

- Install firefox through wine exacly as you would do in windows
Just browse to where you downloaded it, right click on it and "Open with wine Windows Emulator" should appear as an option.
Then NEXT->NEXT->NEXT->FINISH as always.

- Go to youtube and install the flash plugin exactly as you would do in windows.

- Install your addons... etc 
I mean you should be able to continue from here

- That's it

NOTES:

>>> Quicktime:
To install the quicktime support simply download quicktime (windows version of course) and install it with wine. It will problably black out your screen the first time you use it, but it will reapper shortly as you clck around and from then on it will just work.

>>> Windows Media Video ( *.wmv)
This has been tricky.
I tried to install the open source plugin from the Port25 project but it didnt work.
I solved it thanks to this useful Addon 
MediaPlayerConnectivity
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
It allows you to set an external application to play all kind of media files, wmv included.

To configure it, after you installed it, go to Firefox->Tools->MediaPlayerconnectiivity->Configure...
and set something like this for the Windows Media files
Z:\usr\bin\vlc
This will use the VLC media player to play your files. You can use the media player of your liking of course.

>>> Java applets

It doesn't work. It crashes firefox for me.
I didn't solve this because i obviusly can't care less.

>>> Flash yes but not sound??

from a shell again:
$ winecfg
Go to the "Audio" tab
Wait a little bit less then forever for it to load (don't worry, it's just tring to fix the dicontinuity in the matrix).
Try to change the Driver from OSS to Alsa.
This solutin was actually needed only on my Debian and not on Ubuntu.

Enjoy.

---

### Post by Xorg.conF on 2007-09-09
thx for the tip, I HATE when firefox freezes at flash sites, it happens a lot.  Did you ever try to install flash player 7 instead of 9??, I want to know if that method failed.

---

