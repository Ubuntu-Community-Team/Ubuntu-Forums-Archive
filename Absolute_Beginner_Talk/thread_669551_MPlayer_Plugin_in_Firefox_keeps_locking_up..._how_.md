---
title: "MPlayer Plugin in Firefox keeps locking up... how to fix?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2008-01-16
I'm running Ubuntu 7.10 and have the Mplayer Plugin for FIrefox installed. My end goal is to be able to watch movie trailers from Apple.com/trailers 

I open the website in Firefox, I click on Trailer, MPlayer Plug in gives me a white window that shows me the download of the trailer has started and then it's replaced with the wording:

"Playing [http://movies.apple.com/movies/blah](http://movies.apple.com/movies/blah) blah blah/moviename.mov"

a blank status bar is at the bottom of the page.

I wait for around 10-15 minutes and try to close the Web Browser and it is hung. I have to "Force Quit" for it to close. 

I've uninstalled the plugin, rebooted, but I'm not having any luck trying to find another plugin that works in firefox so it looks like I'm stuck using MPlayer.

How do I troulbeshoot this issue to find out why it's broken?

---

### Post by talzz2 on 2008-02-06
I have the same problem but did not realize it was from MPlayer I get this on random websites I have been visiting... I also installed this to try and get QuickTime to play. I will uninstall and see if I still get lock ups..

When visiting websites any websites and have multiple websites open out of no where it just freezes and you have to hit close twice to get it to force in order to get a browser back. Anyone have any ideas other than un installing mplayer???

---

### Post by kerignell on 2008-02-12
I am experiencing the same problem. It works for a while (hours), but then when mplayer plugin is running it freezes firefox up.

Ubuntu 7.10 Gutsy Gibbon X86_64 on an AMD Athlon X2 , Firefox 2.0.0.12, mozilla-mplayer 3.40

---

### Post by talzz2 on 2008-02-12
I know this is not the best fix and only side steps the problem however if you download firefox from the mozilla website and then use these instructions to install

[http://support.mozilla.com/kb/Installing+Firefox+on+Linux#Ubuntu_7_10](http://support.mozilla.com/kb/Installing+Firefox+on+Linux#Ubuntu_7_10)

then you can use the Stand alone version that is not built into ubuntu and I have not had a problem (i have to say I have not watched videos)  I was having random lock ups that I think was caused by having multiple windows or gmail chat open and doing this so far I have not had a lock ups......

I guess I need to open videos and test this.... but I did take advise and installed Opera and this browser works very well I just can not figure out how to get the google toolbar installed.. it does have widgets but would like the tool bar to sit up top (((( i have to admit I have not researched this i've just fooled around with it for a few seconds..)))

---

### Post by vortex0007 on 2008-02-12
talzz2,

It would be more useful if you would take a minute to go to apple.com/trailers and pick a trailer and attempt to watch it. Tell us if your web browser locks up.

---

### Post by talzz2 on 2008-02-12
I have to agree

I can not get the trailers to work in ubuntu firefox or standalone firefox now keeps asking for the plug in

I have it installed and it ""was"" working I have gone back through

[http://www.debianadmin.com/install-mplayer-ubuntu.html](http://www.debianadmin.com/install-mplayer-ubuntu.html) 

I can not figure out my wrong turn

---

### Post by talzz2 on 2008-02-12
ok I got it to work with out locking up going to apple.com/trailers had a quick blip with the sound but closed out of firefox all the way relaunched and it appears to cleared up ...

first I did the current mplayer install from 
[http://www.debianadmin.com/install-mplayer-ubuntu.html](http://www.debianadmin.com/install-mplayer-ubuntu.html)

then I downloaded SMPlayer [http://smplayer.sourceforge.net/downloads.php?tr_lang=en&PHPSESSID=2f6d7d32a3b3418e4e675a63e43a9f3b](http://smplayer.sourceforge.net/downloads.php?tr_lang=en&PHPSESSID=2f6d7d32a3b3418e4e675a63e43a9f3b)

Ialso read on this same forum somewhere in another post that installing xine-plug in works for some reason (it says to install xine-plugin then reinstall mplayer) I can not find the post for the life of me

so I went to the synaptic package manager and installed xine-plug, and gxine-pugin,,  and read also try VLC so while I was there I installed the VLC plug in which installed 12 or 13 other dependent files

now when i go into firefox and play apple.com/trailers they are working with out locking up just fine... They are pulling up with ""Totem Movie Player" "Movie player using gstreamer 0.10.14 and gnome" 



I know this is alot and really not the right way but it is working for me so far so good hope this helps

---

