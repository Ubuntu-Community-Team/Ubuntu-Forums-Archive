---
title: "Installing"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by GaMeFaNaTiC on 2007-09-11
hi, im new to linux and im trying to learn how to use the terminal because it is prob needed to do a lot of things like installing programs etc. 

i downloaded alsa-driver-1.0.14 from the net which came in a bz2 file extension. it opened in some program and i extracted the folder inside of it. i understand that i have to use the terminal to install the drivers using this folder but how do i do it?. 

my alsa-mixer does not work and gives me that invalid argument error. i think my alsa drivers are not working properly although the sound is working but i cannot record and can only use the playback features instead of the capture settings. maybe if i update the drivers these settings will come up. can any1 help plz thanks.

(im using ubuntu with kde desktop).

---

### Post by mlentink on 2007-09-11
There's a [sticky in this forum]("http://ubuntuforums.org/showthread.php?t=500020") about how to install things in Ubuntu, quite comprehensive.

I'd suggest you read that first. 
Basically, I wouldn't recommend installing from source to a beginner, but if you follow the procedure there's really not much to it. 
Unpack the archive
Got into the directory with the source
```
sudo make install
```

Be sure you have gcc (the compiler) and make installed, otherwise install them with 
```
sudo apt-get install build-essentials
```


Good luck..

---

### Post by GaMeFaNaTiC on 2007-09-11
thanks for the link il have a read at it and try to understand it.

---

### Post by mlentink on 2007-09-11
[This]("http://monkeyblog.org/ubuntu/installing/") is also a very good one.

---

### Post by GaMeFaNaTiC on 2007-09-11
thank you looks easier to understand. maybe il read that first then the other one.

---

