---
title: "rhythmbox/gstreamer codec problem"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-02-13
hi,

i just installed ubuntu edgy a few days ago and now i'm at the stage where i get everything to work.

however, i encountered problems getting rhythmbox to play mp3 files. also, serpentine wouldn't record an audio cd from a bunch of mp3 files. i read that i had to download and install the gstreamer codec pack. i did the following:

sudo apt-get install gstreamer

and it installed a whole bunch of codecs. but still no luck, rhythmbox won't play the files and serpentine won't record the cd. a few days ago i installed the missing codecs to amarok, and it works perfectly well.

can someone please tell me what i am doing wrong? 

thank you.

---

### Post by Rhubarb on 2007-02-13
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

You'll need to install a bit more than "sudo apt-get install gstreamer", this should get you going:

Make sure you've enabled access to the restricted and multiverse repositories first:
System --> Administration --> Software Sources
Check restricted and multiverse (all the check boxes should be checked).
Update the sources list (you'll be prompted to do so), then in a terminal:-
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by annda on 2007-02-13
sorry that i can't be more specific, but maybe try to search for gstreamer in synaptic. maybe you will find something that you haven't installed.

also, automatix2 is good for installing codecs and more - if you don't mind using gui tools that tell you little about what they are doing.
[http://www.getautomatix.com](http://www.getautomatix.com)

EDIT: oops, too late again.

---

### Post by shadowboxer_k on 2007-02-13
thanks, guys!

Rhubarb, i followed your advice and it worked! :) thank you again.

---

