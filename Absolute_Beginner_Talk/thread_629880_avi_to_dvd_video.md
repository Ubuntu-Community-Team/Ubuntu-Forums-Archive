---
title: "avi to dvd video"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-12-02
I have been looking at the forums here and it doesn't seem that gnome has a gui/tool to convert avi files to dvd video? Must I use something like kino or the command line?

I would prefer not to install kde apps on my gnome system and I am curious if there is a grandma point 'n click way to do the conversion?


thanks

---

### Post by daimaru on 2007-12-02
```
sudo apt-get install devede
```

EDIT: sry its probably not in the repository. (dont recall). if not go to getdeb.net

or use the link . [http://www.getdeb.net/download.php?release=1712&fpos=0](http://www.getdeb.net/download.php?release=1712&fpos=0)

---

### Post by goodmanbrown on 2007-12-02
I tried a few of the gui tools like devede and tovid, but I ended up settling on command-line tools.  Until the gui tools mature a little, it's much simpler.  Here's a tutorial that makes burning DVDs from AVIs a cinch:

[http://forum.freespire.org/archive/index.php/t-5328.html](http://forum.freespire.org/archive/index.php/t-5328.html)

---

### Post by daimaru on 2007-12-02
thanks goodmanbrown, i'll keep that link for my collection. since command line works 100% of time.

---

### Post by Hospadar on 2007-12-02
devede is in the repository, you might have to enable your multiverse and universe repositories in System->Administration->Software sources, you should use the repo version as opposed to the getdeb version (just for ease of install and uninstall)

Also, while dvd is a great general purpose solution if you just need to drop some videos on a DVD, there are some other options for more control of the transcoding.

If you find you want more than is supplied with devede, try combo-ing avidemux and qdvdquthor.  qdvdauthor is for KDE, but in my opinion the most stable and well featured solution for building dvd menus and such.  Avidemux has some good auto options for dvd video, as well as a whole load of filters to do what you want.

I generally use devede for single files (like movies) but then use avidemux to transcode and qdvdauthor to to build the menus and create the dvd file structure/.iso

---

### Post by siciliancasanova on 2007-12-02
avidemux works for me.  I just used it to convert some videos to xvid and double checked the codecs and you can certainly convert it to dvd.

It's pretty straight forward also, you open up the avi file, select the encoding for the video and audio, (use the calculator button to change the size if you need it and hit apply) and then save the file and it encodes it.

---

