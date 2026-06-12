---
title: "Getting sound but no video playing back dvds and .vob"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by john.burgin on 2007-05-29
I am running feisty on a dell pc, and fairly new to linux.  I've had to contend with some awfully difficult stuff, and have got through most of it with the help from fellow users.

I have a Rapsody external multimedia drive, and an usb external dvd drive.  After (largely randomly) installing various codecs and libraries I can get sound out of .vob and dvd files using codeine, but not totem et. al.  I cannot get video out of codeine, nor anything else.  Applications that won't work at all just close immediately after asking them to play content, codeine will play sounds but without video.

What could be the problem?

Many thanks in advance,

john

---

### Post by Inxsible on 2007-05-29
you might have to install libdvdcss2 from the medibuntu repositories. They are also available on the videolan reps..
 
[www.videolan.org]("http://www.videolan.org")
 
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)
 
Follow the instructions on either sites to install it.
 
Note: They may or may not be available thru synaptic...just that I havent tried it. I installed from the Medibuntu reps and everything works for me :)

---

### Post by john.burgin on 2007-05-29
Ah, but I've already installed libdvdcss2.  Could it be anything else?

John

---

### Post by Inxsible on 2007-05-29
How about libdvdread ?
 
There are a couple more..but i forget their names.
Medibuntu installs all thats needed. So if you installed all, then I am not really sure
 
Can someone else help us out here ?

---

### Post by john.burgin on 2007-05-29
I have that installed also.  A conundrum.  

John

---

### Post by john.burgin on 2007-05-29
Interesting.  If rhythmbox is open then they play in totem (no xine) - albeit sluggishly.

John

---

