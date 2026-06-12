---
title: "[SOLVED] Flash not loading properly"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by kristus on 2008-01-08
I have a problem with my flash-player for firefox (and elsewhere). 
I have the following installed, and I have tried to reinstall them all:
flashplugin-nonfree
libflash-mozplugin
libflash0c2

The problem I get is that when I for instance to to youtube, I will get the whole box where the video is supposed to be, with buttons and everything - and even the "loading"-animation that looks somewhat like a flower.
But it does not load. Nothing happens.

Any suggestions?

---

### Post by Raptor45 on 2008-01-08
Have you tried any other flash sites? Is it possibly a youtube issue, and not your computer?

---

### Post by kristus on 2008-01-08
Well, on for instance myspace all buttons will flash around and behave like maniacs.

---

### Post by jflarm on 2008-01-08
Here is what I did:
1.-I removed the flashplayer with Synaptic
2.-Downloaded the tar file from adobe:  

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
3.-I "untared" it :

tar xvzf install_flash_player_9_linux.tar.gz
4.- and using a terminal ran the flashplayer-installer :
./flashplayer-installer

Hope this helps....

---

### Post by kristus on 2008-01-08
Well. Thank you, but preferably I would like to use the splendid packet-manager and thus keep my system sane and consistent.

---

### Post by caravel on 2008-01-08
Hmmm... I'm not a big youtube user and not much of a flash user either as I'd forgotten to install it!  It may be that it's not flash that is the problem but something to do with the videos themselves?  A codec or a media player issue?

---

### Post by kristus on 2008-01-08
I have now successfully excorised the malicious loa that has plagued my life for so long.
It was gnash. An alfa-stage open source flash implementation with many bugs. 

If others have this problem. Try getting rid of this loa.

---

### Post by jflarm on 2008-01-08
> **kristus said:**
> Well. Thank you, but preferably I would like to use the splendid packet-manager and thus keep my system sane and consistent.

Well...this is just one file...
I had your same problem and this is the way I solved it...if you want to remove it later, just delete the file from the "/usr/lib/mozilla/" directory and check  typing "about:plugins" in the address bar of the firefox.
If you want to keep track of what you've done, take notes in a notebook or use the Tomboy notes (that's what I do).

---

### Post by Sef on 2008-01-08
> I have now successfully excorised the malicious loa that has plagued my life for so long.
It was gnash. An alfa-stage open source flash implementation with many bugs.


Alpha stage software is known for bugs.  I like it being open source, but just is not up to speed yet.

---

