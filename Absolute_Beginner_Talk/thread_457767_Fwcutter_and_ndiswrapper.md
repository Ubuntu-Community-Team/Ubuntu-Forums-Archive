---
title: "Fwcutter and ndiswrapper"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by dixynormus on 2007-05-29
Linux is freakin abusive, i love it except for the fact i cant get my f-in broadcom wifi adapter in my hp laptop to werk,, because fwcutter and ndiswrapper are nowhere to be found on my ubuntu 7 cd nor in the synaptics.  Any takers on this prob?

---

### Post by Ek0nomik on 2007-05-29
You can download ndiswrapper and compile it from source if you want.

[http://umn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.45.tar.gz](http://umn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.45.tar.gz)

There is a link to download.

Once you extract the tarball, you can look at the README file and it will tell you how to compile.

Before you start to compile, make sure you install build-essential (if you have never compiled before)

```
sudo aptitude install build-essential
```

---

### Post by dixynormus on 2007-05-29
I amm nooob i have no idea how to compile loool, care to explain me lol . thx

---

### Post by Ek0nomik on 2007-05-29
This is a bit outdated, but it may help:

[http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source](http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source)

Basically, once you have the tarball, extract it.  Go inside the directory, and read the README file with your text editor (gedit, nano, etc).

The commands generally go in this pattern.

```
./configure
sudo make
sudo make install
```

---

### Post by rondackcpu on 2007-05-29
Welcome, noob.  I was a noob a couple of months ago, and you'll get the hang of it quickly.  Under System>Administration>Software Sources check to see that all the sources boxes are checked.  Once that is done, the system will tell you to reload the files.  Click reload.  Once that is done, the system has a little problem.  Click the upper right hand close box on Software Sources.  System will again ask you to reload.  Ignore.  Click Close again.  The back to System>Administration>Synaptic.  Scroll down and you will find Ndiswrapper now.

Good luck

CRS

---

### Post by Ek0nomik on 2007-05-29
The version of ndiswrapper in the repository is outdated.

I think it is a 1.x version.  I believe ndiswrapper is now at 2.45 or something.  So, keep that in mind.

---

