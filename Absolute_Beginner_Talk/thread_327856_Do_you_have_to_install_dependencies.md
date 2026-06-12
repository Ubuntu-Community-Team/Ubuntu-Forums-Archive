---
title: "Do you have to install dependencies???"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-12-29
As I currently do not have an internet connection on my box running Ubuntu dapper, It seems that some programs need 2 dependencies or so, but once i get onto this computer and go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and download what I need to run my program.....The extra files that they needed i.e.libxine-main etc... need dependencies themselves(about 5 or 6). My question is, is there a command when installing using dpkg to force the install and configuration of such a file without having to download all the other dependencies. Which in turn im guessing would have dependencies themselves(Is it a never ending cycle??)

---

### Post by kinematic on 2006-12-29
dependencies are there for a reason....otherwise the program won't work....just let the packaging system do it's job.
but there is a way of handling it better by using aptitude.
aptitude handles dependencies better than apt-get and if you want to uninstall an app aptitude also removes the dependencies.

---

### Post by Frak on 2006-12-29
Dependencies usually don't have their own dependencies, and without those dependencies, the program can't run, because its probably coded in another language or it is a part of the program, and instead of including that same library or part in every download, you have dependencies, which allow's the user to save space by using the one a bunch of times.

---

### Post by nite owl on 2006-12-29
hmm so I'm guessing my first priority now should be getting the internet working on my Linux box. Then I can get my dvds playing.

---

### Post by Frak on 2006-12-29
> **nite owl said:**
> hmm so I'm guessing my first priority now should be getting the internet working on my Linux box. Then I can get my dvds playing.
Ubuntu's nothing without the Globall Intarweb.

---

### Post by nite owl on 2006-12-29
Alright well atleast I know now. Thanks for all your help this really is the best community :)

---

### Post by Some_Person on 2006-12-29
To simply put it, yes, you do need to install dependencies. But if you don't have internet on Ubuntu, just download the dependencies you need from [here](http://packages.ubuntu.com/) and install them.

---

