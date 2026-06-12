---
title: "OMG! not even funny Desperate Help on build essentials"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Anomaly on 2006-04-04
First thx for any feedback!

](*,) 

the thing is that Im installing a network card and I dont have the internet right now and there is no way to run a wire.  This being said, Im trying to install ndiswrapper from source. To do this I needed the build essentials for the "make" command.

Problem:  I dont know how to install the build essential source. I got the tar, but I dont know the command to install it. Im also assuming its not "make" since that is the program thats supposed to install "make."

thx again.

---

### Post by Anomaly on 2006-04-04
Sry,

        One thing I forgot to mention, I also downloaded the .deb  of the build essentials.  With the tar.  Is it any easier to install?

Thx,
           Anomaly

---

### Post by htinn on 2006-04-04
If you install "build-essentials" it won't do anything for you because that's just a dummy package that tells apt to then download some other stuff.

What you really need is either internet access or to download all the dependencies of build-essentials and sudo dpkg -i them by hand in the proper order (not fun).

[http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential)

---

### Post by stuporglue on 2006-04-04
Anomaly, 

You can download a binary version of ndiswrapper, and use "dpkg -i" to install it. 

-100 headache
+100 time savings

---

### Post by Qrk on 2006-04-04
ndiswrapper is on your install disk. Just pop the disk back into the drive and install it using using synaptic. 

It isn't installed by default, but the developers were nice enough to realize that you may need a way to get it without an internet connection.

---

### Post by Anomaly on 2006-04-05
Thx for all your help guys!

Im at school right now so ill try it as soon as I get home:-D

---

