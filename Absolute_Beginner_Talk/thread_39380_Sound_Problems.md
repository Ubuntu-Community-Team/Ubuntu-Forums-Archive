---
title: "Sound Problems"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by ajsadler on 2005-06-04
Lol, I told you there would be a new problem soon. I have copied over some mp3s from an external hard drive which I used during my reformat, but I tried to open the files but Totem says that they wont play.

"
There were no decoders found to handle the stream in file "file:///home/aj/Desktop/Bob%20Dylan/Bob%20Dylan%20-%20Like%20A%20Rolling%20Stone.mp3", you might need to install the corresponding plugins
"

Any help? Thanks


-AJ

---

### Post by kozmo on 2005-06-04
[QUOTE=ajsadler]Lol, I told you there would be a new problem soon. I have copied over some mp3s from an external hard drive which I used during my reformat, but I tried to open the files but Totem says that they wont play.

"
There were no decoders found to handle the stream in file "file:///home/aj/Desktop/Bob%20Dylan/Bob%20Dylan%20-%20Like%20A%20Rolling%20Stone.mp3", you might need to install the corresponding plugins
"

Any help? Thanks


-AJ[/QUOTE]
try installing the gstreamer-plugins
```
sudo apt-get install gstreamer0.8-plugins
```
If that doesn't work you may need to Google for the codecs.

---

### Post by ajsadler on 2005-06-04
I'm sorry but google for which Codecs exactly? Thanks


-AJ

---

### Post by henriette_holm on 2005-06-04
Take a look at the ubuntu starter guide - [http://ubuntuguide.org](http://ubuntuguide.org) .
Look at the following section: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)


-Henriette

---

### Post by ajsadler on 2005-06-04
aj@AJ:~$ sudo apt-get install gstreamer0.8-plugins
Password:
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
aj@AJ:~$ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-lame
aj@AJ:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=ajsadler]aj@AJ:~$ sudo apt-get install gstreamer0.8-plugins
Password:
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
aj@AJ:~$ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-lame
aj@AJ:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs[/QUOTE]


You need to add some repos. Look at this page for a while:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by ajsadler on 2005-06-04
Thanks everyone again. My saviours lol. Thanks


-AJ

---

### Post by ajsadler on 2005-06-04
Hmmm I got a connection error while downloading all them update things. Once I reconnected I found the little red icon in the tray and it updates everything that needs updating so I've done that (I read in the list of what it updates that it updates Totem and other stuff) and still the music doesnt play :( Anyone help? Thanks


-AJ


Nevermind it now sorry I got it working :) Thanks again for all your guys/gals help I really appreciate it and it's made me love the whole Ubuntu comminity :) Hopefully in a few months time I will be helping the beginners.

---

