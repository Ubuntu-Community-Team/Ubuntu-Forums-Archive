---
title: "flashplayer 9 problem"
date: 2007-12-09
forum: Apple Intel Users
---

### Post by trevelyn on 2007-12-09
sorry i have searched the forums and havent seen a resolve for this issue:

swf files played in the browser play fine, but the sound chirps and gets really annoying.  The sound works fine on my windows machine so i know the sound is okay in the videos.  

any ideas?  I have Gutsy, MacBook, and manually installed the flash 9 from the adobe site.
also, i use camtasia to make videos and embed mp3's into them, i dont know if anyone ever heard an mp3 skip, but it's a high pitched chirp, or squealing sound...


- thanks in *gameboy* advance - Trev.

---

### Post by daradib on 2007-12-09
Please try again with installing Flash 9 through this method: [http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

---

### Post by trevelyn on 2007-12-09
yeah i followed those directions perfectly, waited for the deb to install in the GUI and rebooted my machine.  Opened my html that hosts my swf file, and sure enough it's still bad.  Youtube videos play fine.  but swf videos dont.  exempli gratia screencasts from offensive security, or screencasts i make with camtasia. 

the video looks fine, its just the sound.  I put them on my keydrive and play them on the macbook pro, they sound perfect... ???

???


maybe my MacBook 2GB RAM:

vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB

can't handle flash + ubuntu? :(

---

### Post by daradib on 2007-12-09
This probably does not seem to be a flash problem, as you do have a problem with MP3s as well.

[https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d](https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d)
[http://www.finefrog.com/2007/07/31/ubuntu-macbook-sound/](http://www.finefrog.com/2007/07/31/ubuntu-macbook-sound/)

MacBookPro: [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)
MacBook Santa Rosa: [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by trevelyn on 2007-12-09
okay i did that during the install,

but your right about something, firefox does not play mp3's the way it does wav files.

i have issued 

"apt-cache search mp3 | grep mozilla"
"apt-cache search mpeg | grep mozilla"
"apt-cache search mp3 | grep firefox"

etc etc etc ... installed every plugin thing i could that said swf mozilla.  so far nothing is working :S  after googling for a while i found someone else with the same problem but didnt find a solution (except to save every flv from youtube onto his hdd for local playback which im not going to do)  Youtube plays ok and they are flv.  i can extract mp3's from flv.  heres a quick example:

[http://www.milw0rm.com/video/watch.php?id=53](http://www.milw0rm.com/video/watch.php?id=53)

this flv plays perfectly... and theres an mp3 in it. ???

???

=============

edit: I can open say: file:///home/trevelyn/Desktop/song.mp3 and it plays fine and says "(no video)" in white letters against a black bg.
but if its in swf its garbled.

---

### Post by daradib on 2007-12-10
I don't have an answer. Bumping you if someone else can give a better answer. Just search the forums if you haven't done so already.

---

### Post by trevelyn on 2007-12-11
i did, thank you very much i can't figure it out.  Also my battery monitor just died.  0% all the time, even when the LED indicator on the battery says %100.  I remeber that happened before with feisty but, i couldnt fix it back then.  I will search the forums before posting to ask advice.

- trevelyn.

---

