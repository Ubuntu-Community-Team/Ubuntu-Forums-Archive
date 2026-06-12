---
title: "Downloading Apps."
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Robert98374 on 2007-04-17
Please tell me that i am wrong but do i have to be connected to the internet to be able to download applications? Or is there someway to download them on another  computer and then  transfering them by Cd?

i found a website i can download from it but the files are extremely small and i was wondering if it was like a torrent-like system?
the link is [Clicky]("http://http://packages.ubuntulinux.org/edgy/")

---

### Post by Rui Pais on 2007-04-17
> **Robert98374@yahoo.com said:**
> Please tell me that i am wrong but do i have to be connected to the internet to be able to download applications? Or is there someway to download them on another  computer and then  transfering them by Cd?

i found a website i can download from it but the files are extremely small and i was wondering if it was like a torrent-like system?
the link is [Clicky]("http://http://packages.ubuntulinux.org/edgy/")

Yes, but don't do it that way. 

Linux use a package management to deal with software applications, it's graphical interface is called synaptic.

Search for it on menu: System -> Administration -> Synaptic

---

### Post by Robert98374 on 2007-04-17
Yes? sorry i am a little ding bat right, but what do you mean by the yes part? That i am able to install it that way or yes i have to connect using the computer thats running linux right now?

---

### Post by Bias on 2007-04-17
You should be able to use files burnt to a cd, the files normally are quite small.

Try it with one or two apps on a cd then start synaptic and click on settings and then repositories, you will see a button "Add CD ROM" click on it and you should be good to go. :)

Nick.

---

### Post by Robert98374 on 2007-04-17
Alright i will try it out :-)
Btw thanks for all the help guys if this forum wasnt so widly used and answerd i am not sure if i would use ubuntu

---

### Post by Rui Pais on 2007-04-17
> **Robert98374@yahoo.com said:**
> Yes? sorry i am a little ding bat right, but what do you mean by the yes part? That i am able to install it that way or yes i have to connect using the computer thats running linux right now?

oops, sorry i misread your post. :(

the apps are packaged as deb files. If you click on a deb file an app, called gdebi will install it.

So if you download for a computer or burn to a cd debs of the app you want you can clic on them.
But you may hit some dependencies needs and you should avoid mixing versions or even bad mixing debian packages with ubuntu packages.

If possible always use synaptic or command line apt.

---

### Post by zvacet on 2007-04-17
If you don´t have intrnet on your ubuntu comp it is possible to download from other comp.burn on disc and install on Ubuntu.You mast be very carefull,because maybe you need to download dependencies with package.In short yes you can do it but download all you need.

---

### Post by Robert98374 on 2007-04-17
Alright will use the synaptic, now i am wondering if that program also makes sure that the file will be usable with this version of Ubuntu?

---

### Post by christhemonkey on 2007-04-17
You do have to be connected to the internet to use the builtin synaptic/apt tools.

Thankfullly for some thats not the only way!

You can indeed use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but when you search for a program, say for an example, erm, mc-foo, which is a mp3 jukebox type thing, you need to not only get the mc-foo_0.0.13ubuntu1_all.debbut also the dependencies which are listed underneath:

> 
python (<< 2.5)
python (>= 2.4)
python-id3
python-oss
python-pmw (>= 0.8.5-3)
python-pymad
python-pyvorbis
python-tk
python-twisted


Which depend on a whole list more of applications... which you need to get all the dependencies for... who you need to get the dependencies for... oh the joy!! :D

Its not too bad when you learn what sort of things are included by default (ie you dont need to re-get them!)

---

### Post by jvc26 on 2007-04-17
Synaptic only accesses the repositories (online servers with all the apps and their dependencies on) which are corresponding to your version hence everything will be for your version (unless you change the repos list to a different at which point bad things happen) Therefore installation via synaptic will be fine. Also, you are using 5.10 according to your profile which is very old, it may also help for you to get more up to date versions of software to get the new Ubuntu 7.04 when it comes out in a few days time.
Il

---

### Post by qamelian on 2007-04-17
Don't forget that if you are going to try to install applications this way, you need to make sure you grab *all* the dependent packages as well, otherwise you're going to get frustrated doing laps between computers!

---

### Post by Robert98374 on 2007-04-17
Alright well my next question is for example on the [Page]("http://http://packages.ubuntulinux.org/edgy/doc/debian-reference-common") i scroll to the very bottom and click on the all link and download from there?

---

### Post by Robert98374 on 2007-04-17
Sorry about the incorrect version info, fixed it. Thanks for pointing it out :-):popcorn:

---

