---
title: "Quicktime 7 .mov in Ubuntu?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-01-13
Whats the best for this?

XIne?
Mplayer?
VLC?
Totem?

And which codecs should I install?

Thanks,

sv

---

### Post by SOULRiDER on 2008-01-13
Try installing MPlayer and the mozilla-mplayer package so you have the Mozilla plugin. I believe you can play QT in mplayer without installing additional packages, although im not 100% sure. You could also try using VLC. If that fails, yo could install QT7 and use it to play QT videos IMO although its not the "cleanest" solution. You can find a script that will install QT here: [http://frankscorner.org/index.php?p=scripts](http://frankscorner.org/index.php?p=scripts)

Good luck and tell us how it goes.

---

### Post by SOULRiDER on 2008-01-13
I did some more searching and apparently you'll have to install these packages
> libxvidcore4
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
gstreamer0.10-gl
gstreamer0.10-pitfdll
libquicktime0
w32codecs

Install thse packages first and see if you get it to work.

---

### Post by ugm6hr on 2008-01-13
This is absolutely the best solution I have found for Gutsy and Quicktime streaming:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

It just works, allows pause and change location in stream, just like in Windows Quicktime (and presumably OSX).

I've tried it out on the apple trailers ([http://www.apple.com/trailers/](http://www.apple.com/trailers/)), and it works great.

Have to say, I use VLC to play DVDs and other non-streaming video though....

---

### Post by staticvoid on 2008-01-13
hmm... well I'll try all those out...

my players recognize the video but not the audio codecs so far (as .mov is just container for formats)

in windows i can't play my quicktime 7 files very well! Ha! They skip and jibber...

Aparently realplayer in windows played the mov, and as there is realplayer for linux I'll try that...


ok, and thank you ugm6hr for the link, i'll be able to see streaming .mov now!! :D

sv

---

### Post by nikoPSK on 2008-01-13
> **staticvoid said:**
> Whats the best for this?

XIne?
Mplayer?
VLC?
Totem?

And which codecs should I install?

Thanks,

sv

totem, just open it and it will tell you you need the gstreamer plugins and bring you to a window where you can choose to install them.

~/nikoPSK

---

### Post by ubuntu-freak on 2008-01-13
> **ugm6hr said:**
> This is absolutely the best solution I have found for Gutsy and Quicktime streaming:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

It just works, allows pause and change location in stream, just like in Windows Quicktime (and presumably OSX).

I've tried it out on the apple trailers ([http://www.apple.com/trailers/](http://www.apple.com/trailers/)), and it works great.

Have to say, I use VLC to play DVDs and other non-streaming video though....

 
Thanks for the endorsement! :) 
 
I'm obsessive so had to get streaming working. Tried to include everything for the newbies too (links, alternative non broken flash, java etc). 
 
Thanks, 
 
Nathan

---

### Post by ugm6hr on 2008-01-13
> **reassuringlyoffensive said:**
> Thanks for the endorsement! :) 


Credit where it's due!

I use BBC and Apple Trailer streaming, and your solution was the only one that got me usable results with Apple.

---

