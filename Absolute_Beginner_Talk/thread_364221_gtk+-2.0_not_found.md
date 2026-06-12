---
title: "gtk+-2.0 not found"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by adza on 2007-02-18
I am trying my first install using the ./configure, make etc way of doing things and have come accross what i believe is referred to as 'dependancy hell' hehe. Ater installing several packages from synaptic and re running the ./configure i am not getting the message ..

checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8) were not met:  **this was the number 8... nice spot for a smiley though***

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I don't like the option of setting env variables at this stage of my linux career... however i can't find anything in synaptic that resembles this package? Could anyone help?

---

### Post by yabbadabbadont on 2007-02-18
libgtk2.0-dev

---

### Post by adza on 2007-02-18
excellent yabba... just found that one :) it just got me to my next dependancy... hehe

---

### Post by yabbadabbadont on 2007-02-18
xorg-dev will get you a lot of build dependencies.  If the software you are trying to build is in the repositories, but you are building a newer version (I do that all the time), then you can usually get all the build dependencies by running, "apt-get build-dep packagename".

---

### Post by adza on 2007-02-18
now that is a handy tip! does that work with 'un-official' repositories as well? ie, any repos in the sources.list?

---

### Post by yabbadabbadont on 2007-02-18
The definitive answer is... maybe.  ;)  It depends entirely upon how the 3rd party built their deb files (and package list files probably).  If they put the full, correct information in them when they created them, then it should work.  You probably should run, "apt-get -s build-dep packagename" first to see what it would do.  (just in case)  It's also possible that the 3rd party used different package names for the build dependencies than those used by the official repositories.  That isn't too uncommon an occurance by the way.  I guess the short answer is, try it and see what happens.  :D

---

### Post by adza on 2007-02-18
okay...i will try that on the next install - i'm kinda enjoying this at the moment (i know - sick puppy indeed, right for linux? hehe) i'm trying to build banshee btw.... got another one.. i've installed everything off synaptic i can find even close to this!!

checking for AVAHISHARP... configure: error: Package requirements (avahi-sharp) were not met:

No package 'avahi-sharp' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AVAHISHARP_CFLAGS
and AVAHISHARP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


any suggestions?

---

### Post by yabbadabbadont on 2007-02-18
Have read through this?

[http://www.ubuntuforums.org/showthread.php?t=327423&highlight=howto+banshee](http://www.ubuntuforums.org/showthread.php?t=327423&highlight=howto+banshee)

---

### Post by adza on 2007-02-18
here you go, putting facts into the story again! that was very good.... banshee is up and running... i had to enable the multiverse in the repository and the build dependancies thing you mentioned above worked a treat :) no to install the ipod plugin... adding files and vid to the ipod is the last thing keeping the windows drive alive.....

---

### Post by yabbadabbadont on 2007-02-18
Have you seen these?

[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

And

[http://www.ubuntuforums.org/showthread.php?t=114946&highlight=video+ipod](http://www.ubuntuforums.org/showthread.php?t=114946&highlight=video+ipod)

---

### Post by H.E. Pennypacker on 2007-02-18
> **yabbadabbadont said:**
> libgtk2.0-dev

This applies to a lot of similar dependencies.  When you're told you don't have something, look for something by the same name, but with -dev at the end.  

I don't know why this is so.

---

### Post by adza on 2007-02-18
yabba, i hadn't seen those yet... however they appear to be just what i need... thanks for all your help... kudos to you :)

---

