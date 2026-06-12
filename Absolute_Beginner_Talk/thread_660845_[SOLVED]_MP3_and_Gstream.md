---
title: "[SOLVED] MP3 and Gstream"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by thenailedone on 2008-01-07
Ok... so I have to download packages via XP then install on Gutsy... I would like to get multimedia support in Gutsy... so far I have found the libdvdcss2 package to get the DVD working (still have to install).

When trying to open any avi or MP3's I get the search for suitable codec error and I see Gstream is the codec it wants to install... where will I find the required packages to install this or is their a better alternative (I did install the W64codecs from medibuntu and I don't seem to have more success viewing/listening to any files)?

Thx

---

### Post by Flyingjester on 2008-01-07
[www.medibuntu.org](www.medibuntu.org) has the required codecs for mp3 support, as well as streaming.

---

### Post by thenailedone on 2008-01-08
> **Flyingjester said:**
> [www.medibuntu.org](www.medibuntu.org) has the required codecs for mp3 support, as well as streaming.

...thanks for the reply but I have been unable to find the Gstreamer codecs on Medibuntu... the couple of packages that I have downloaded from Medibuntu thus far have all installed correctly (didn't have any dependency issues etc.)... they were the libdvdcss2 and the W64codecs but as soon as I try and open a movie (avi) or play music (MP3) it still tries and download the Gstreamer codecs... (I tried Rhythm Box and Totem)...

Am I missing something... are there additional steps required...?

---

### Post by forestpixie on 2008-01-08
you'll need to get the gstreamer codecs I expect then - look here, I have a fair few installed - you might need the good, the bad and the ugly 

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=gstreamer&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=gstreamer&sourceid=mozilla-search)

---

### Post by thenailedone on 2008-01-08
> **forestpixie said:**
> you'll need to get the gstreamer codecs I expect then - look here, I have a fair few installed - you might need the good, the bad and the ugly 

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=gstreamer&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=gstreamer&sourceid=mozilla-search)

Just had a look at the "good" and all of the dependencies (and the dependencies dependencies)... holy @#$%@#... this is going to take forever... until X-Mas even :(

---

### Post by forestpixie on 2008-01-08
yea it's a bit of a problem without the net - but there are a few things here about getting stuff without net connection

have alook at these they might be of help

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)
[http://ubuntuforums.org/showthread.php?t=588191&page=2](http://ubuntuforums.org/showthread.php?t=588191&page=2)
[http://www.ubuntu-hr.org/proba.php](http://www.ubuntu-hr.org/proba.php)
[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

guess you've not got net sorted out yet :(

---

### Post by thenailedone on 2008-01-10
> **forestpixie said:**
> yea it's a bit of a problem without the net - but there are a few things here about getting stuff without net connection

have alook at these they might be of help

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)
[http://ubuntuforums.org/showthread.php?t=588191&page=2](http://ubuntuforums.org/showthread.php?t=588191&page=2)
[http://www.ubuntu-hr.org/proba.php](http://www.ubuntu-hr.org/proba.php)
[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

guess you've not got net sorted out yet :(

Wow... nonetdebs FTW!

Ok, so I (apparently) already had the good installed... installed the bad and the ugly and... I can watch my movies... now I can waste tremendous amount of time watching anime... o.0

So... music is sorted and movies are sorted (I can watch all types except real media via totem but I got it working when I installed gxine)...

BUT when I try and watch DVD's in totem all I get is sound... which is a start but I like pictures too... so I installed gxine (which I thought would solve my problems)... and it doesn't want to play my DVD's either (it cries something about no demuxer being installed or something...)

Any assistance with DVD playback would be greatly appreciated but... if not I will start a new thread :p

---

### Post by forestpixie on 2008-01-10
seems like years ago - when it's in fact just 1 - had a problem with mplayer with no video

if that's what you're using try opening preferences in mplayer
got to the video tab and make sure that xv is selected, then close and try again

it could just as easily not be that but ... :)

---

### Post by rhc on 2008-01-10
What about the vlc player?

---

### Post by thenailedone on 2008-01-10
> **forestpixie said:**
> seems like years ago - when it's in fact just 1 - had a problem with mplayer with no video

if that's what you're using try opening preferences in mplayer
got to the video tab and make sure that xv is selected, then close and try again

it could just as easily not be that but ... :)

...I'm not using mplayer... using Totem and newly installed gxine... would you recommend me trying mplayer?

---

### Post by forestpixie on 2008-01-10
I prefer it myself, the way I see it - especially given that there is such an enormous choice, is that if it works for you and does all you want at the right time without any mucking about - go for it

 - but let's not turn this thread into one of those 'I prefer' threads or it'll be 30 pages long by the time you turn round.

I do also use vlc for some files, but it isn't my first choice.

:D

---

### Post by thenailedone on 2008-01-10
> **forestpixie said:**
> I prefer it myself, the way I see it - especially given that there is such an enormous choice, is that if it works for you and does all you want at the right time without any mucking about - go for it

 - but let's not turn this thread into one of those 'I prefer' threads or it'll be 30 pages long by the time you turn round.

I do also use vlc for some files, but it isn't my first choice.

:D

Fair enough (I actually use VLC on windows because of it's out of the box support for many file types :) )

---

