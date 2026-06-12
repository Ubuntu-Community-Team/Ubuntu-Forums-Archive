---
title: "Amarok and Xine Engine"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by WarholsGhost on 2007-09-17
Hello

So i am running amarok and it is using xine. It makes my computer lag and do weird things like freeze up every once in a while. I would like to change to the gstreamer that linux offers, but how do i install it and make it work with amarok?

thanks in advance.

---

### Post by Clay_Banger on 2007-09-18
before u change it from xine, how big is your music collection? large music collections can cause amarok to have small freezes which can be fixed by changing the method amarok uses to store you music library over to mysql, instead of sqlLite.

---

### Post by WarholsGhost on 2007-09-18
my collection is on the large side. how can i change how amarok stores my music?


> **Clay_Banger said:**
> before u change it from xine, how big is your music collection? large music collections can cause amarok to have small freezes which can be fixed by changing the method amarok uses to store you music library over to mysql, instead of sqlLite.

---

### Post by Clay_Banger on 2007-09-18
heres a how-to:
[http://ubuntuforums.org/showthread.php?t=440918]("http://ubuntuforums.org/showthread.php?t=440918")

and if you have any troubles with that, heres the amarok with mysql wiki page:
[http://amarok.kde.org/wiki/MySQL_HowTo]("http://amarok.kde.org/wiki/MySQL_HowTo")

---

### Post by WarholsGhost on 2007-09-20
I used the second one to set it up and now when i log in through amarok none of my files show up

I'm not getting any error pop=ups so i'm at a loss

---

### Post by stmiller on 2007-09-20
Amarok only uses xine.

---

### Post by WarholsGhost on 2007-09-21
thanks, do you have any experience with mysql?

---

### Post by Clay_Banger on 2007-09-23
did you rescan & update your collection? and make sure that your music folder is selected in the collection part of the settings.

---

### Post by AndyCooll on 2007-09-23
There is an "amarok-engines" pack in the repos which you can install. IIRC, that installs extra engines and hence giving you a choice, though I can't ever remember gstreamer being one of those alternatives.

:cool:

---

### Post by crav on 2007-09-23
> **AndyCooll said:**
> There is an "amarok-engines" pack in the repos which you can install. IIRC, that installs extra engines and hence giving you a choice, though I can't ever remember gstreamer being one of those alternatives.

:cool:
 I installed that package, but the Amaork Configuration screen doesn't have any options other than xine, is there a way to access these?

Also: I have something messed up with my xine where it STILL (I've done everything) doesn't play mp3s, so having another engine would be great.

---

### Post by hyperair on 2007-10-24
There is only one amarok engine available at the moment, and that's xine. Amarok-engines is a metapackage which refers to all the Amarok engines available, and since only Xine is available, that's all you get.

---

